Para criar um projeto Java com registro e autenticação de usuário e banco de dados, você pode usar o Spring Boot, que é um framework que simplifica o desenvolvimento de aplicativos Java. Aqui está um exemplo de como você pode fazer isso:

1. **Crie um novo projeto Spring Boot**

Primeiro, crie um novo projeto Spring Boot. Você pode fazer isso usando o Spring Initializr (https://start.spring.io/). Selecione as seguintes dependências: Spring Web, Spring Security, Spring Data JPA e H2 Database.

2. **Crie uma entidade `User`**

Em seguida, você pode criar uma entidade `User`. No diretório `src/main/java/com/example/demo`, crie um novo pacote `model` e adicione o seguinte código:

```java
package com.example.demo.model;

import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;

@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private Long id;
    private String username;
    private String password;

    // getters and setters
}
```

3. **Crie um repositório `UserRepository`**

Agora você pode criar um repositório `UserRepository`. No diretório `src/main/java/com/example/demo`, crie um novo pacote `repository` e adicione o seguinte código:

```java
package com.example.demo.repository;

import com.example.demo.model.User;
import org.springframework.data.jpa.repository.JpaRepository;

public interface UserRepository extends JpaRepository<User, Long> {
    User findByUsername(String username);
}
```

4. **Crie um serviço `UserDetailsService`**

Em seguida, você pode criar um serviço `UserDetailsService`. No diretório `src/main/java/com/example/demo`, crie um novo pacote `service` e adicione o seguinte código:

```java
package com.example.demo.service;

import com.example.demo.model.User;
import com.example.demo.repository.UserRepository;
import org.springframework.security.core.userdetails.UserDetails;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.core.userdetails.UsernameNotFoundException;
import org.springframework.stereotype.Service;

@Service
public class UserDetailsServiceImpl implements UserDetailsService {
    private final UserRepository userRepository;

    public UserDetailsServiceImpl(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    @Override
    public UserDetails loadUserByUsername(String username) throws UsernameNotFoundException {
        User user = userRepository.findByUsername(username);
        if (user == null) {
            throw new UsernameNotFoundException(username);
        }
        return new org.springframework.security.core.userdetails.User(user.getUsername(), user.getPassword(), new ArrayList<>());
    }
}
```

5. **Configure o Spring Security**

Agora você precisa configurar o Spring Security. No diretório `src/main/java/com/example/demo`, crie um novo pacote `config` e adicione o seguinte código:

```java
package com.example.demo.config;

import com.example.demo.service.UserDetailsServiceImpl;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.authentication.dao.DaoAuthenticationProvider;
import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;

@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {
    private final UserDetailsServiceImpl userDetailsService;

    public SecurityConfig(UserDetailsServiceImpl userDetailsService) {
        this.userDetailsService = userDetailsService;
    }

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .anyRequest().authenticated()
                .and()
            .formLogin()
                .loginPage("/login")
                .permitAll()
                .and()
            .logout()
                .permitAll();
    }

    @Override
    protected void configure(AuthenticationManagerBuilder auth) throws Exception {
        auth.authenticationProvider(authenticationProvider());
    }

    @Bean
    public DaoAuthenticationProvider authenticationProvider() {
        DaoAuthenticationProvider authProvider = new DaoAuthenticationProvider();
        authProvider.setUserDetailsService(userDetailsService);
        authProvider.setPasswordEncoder(passwordEncoder());
        return authProvider;
    }

    @Bean
    public BCryptPasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();
    }
}
```

6. **Crie um controlador `UserController`**

Finalmente, você pode criar um controlador `UserController`. No diretório `src/main/java/com/example/demo`, crie um novo pacote `controller` e adicione o seguinte código:

```java
package com.example.demo.controller;

import com.example.demo.model.User;
import com.example.demo.repository.UserRepository;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PostMapping;

@Controller
public class UserController {
    private final UserRepository userRepository;
    private final BCryptPasswordEncoder passwordEncoder;

    public UserController(UserRepository userRepository, BCryptPasswordEncoder passwordEncoder) {
        this.userRepository = userRepository;
        this.passwordEncoder = passwordEncoder;
    }

    @GetMapping("/register")
    public String showRegistrationForm() {
        return "register";
    }

    @PostMapping("/register")
    public String registerUser(User user) {
        user.setPassword(passwordEncoder.encode(user.getPassword()));
        userRepository.save(user);
        return "redirect:/login";
    }

    @GetMapping("/login")
    public String showLoginForm() {
        return "login";
    }
}
```

Este exemplo usa o Spring Boot para criar um aplicativo web, o Spring Security para gerenciar a autenticação de usuário, o Spring Data JPA para gerenciar o banco de dados, e o H2 Database como banco de dados em memória. As páginas de registro e login são criadas usando o Thymeleaf (você precisará criar os arquivos `register.html` e `login.html` no diretório `src/main/resources/templates`).