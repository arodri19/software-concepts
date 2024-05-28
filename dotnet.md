Para criar um projeto .NET com registro e autenticação de usuário e banco de dados, você pode usar o ASP.NET Core Identity, que é um sistema de gerenciamento de usuários que suporta autenticação de usuário, registro de usuário, autorização, gerenciamento de funções, etc.

Aqui está um exemplo de como você pode fazer isso:

1. **Crie um novo projeto ASP.NET Core**

Primeiro, crie um novo projeto ASP.NET Core usando o comando `dotnet new`:

```bash
dotnet new webapp -o MyWebApp
```

2. **Navegue até o diretório do seu projeto**

Depois de criar seu projeto, navegue até o diretório do projeto com o comando `cd`:

```bash
cd MyWebApp
```

3. **Adicione o pacote ASP.NET Core Identity**

Agora você pode adicionar o pacote ASP.NET Core Identity ao seu projeto com o seguinte comando:

```bash
dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore
```

4. **Crie um contexto de banco de dados**

Em seguida, você pode criar um contexto de banco de dados. No diretório `Data`, crie um novo arquivo `ApplicationDbContext.cs` e adicione o seguinte código:

```csharp
using Microsoft.AspNetCore.Identity.EntityFrameworkCore;
using Microsoft.EntityFrameworkCore;

namespace MyWebApp.Data
{
    public class ApplicationDbContext : IdentityDbContext
    {
        public ApplicationDbContext(DbContextOptions<ApplicationDbContext> options)
            : base(options)
        {
        }
    }
}
```

5. **Configure o contexto do banco de dados**

Agora você precisa configurar o contexto do banco de dados. No arquivo `Startup.cs`, adicione o seguinte código no método `ConfigureServices`:

```csharp
services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(
        Configuration.GetConnectionString("DefaultConnection")));
services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
    .AddEntityFrameworkStores<ApplicationDbContext>();
```

6. **Configure a autenticação**

Ainda no arquivo `Startup.cs`, adicione o seguinte código no método `Configure`:

```csharp
app.UseAuthentication();
app.UseAuthorization();
```

7. **Crie uma página de registro**

Agora você pode criar uma página de registro. No diretório `Pages`, crie um novo arquivo `Register.cshtml.cs` e adicione o seguinte código:

```csharp
using System.Threading.Tasks;
using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc;
using Microsoft.AspNetCore.Mvc.RazorPages;

namespace MyWebApp.Pages
{
    public class RegisterModel : PageModel
    {
        private readonly UserManager<IdentityUser> _userManager;
        private readonly SignInManager<IdentityUser> _signInManager;

        public RegisterModel(UserManager<IdentityUser> userManager, SignInManager<IdentityUser> signInManager)
        {
            _userManager = userManager;
            _signInManager = signInManager;
        }

        [BindProperty]
        public InputModel Input { get; set; }

        public class InputModel
        {
            public string Email { get; set; }
            public string Password { get; set; }
        }

        public async Task<IActionResult> OnPostAsync()
        {
            if (ModelState.IsValid)
            {
                var user = new IdentityUser { UserName = Input.Email, Email = Input.Email };
                var result = await _userManager.CreateAsync(user, Input.Password);
                if (result.Succeeded)
                {
                    await _signInManager.SignInAsync(user, isPersistent: false);
                    return RedirectToPage("/Index");
                }
                foreach (var error in result.Errors)
                {
                    ModelState.AddModelError(string.Empty, error.Description);
                }
            }
            return Page();
        }
    }
}
```

E crie um arquivo `Register.cshtml` com o seguinte código:

```html
@page
@model RegisterModel
<form method="post">
    <input asp-for="Input.Email" type="email" placeholder="Email" />
    <input asp-for="Input.Password" type="password" placeholder="Password" />
    <button type="submit">Register</button>
</form>
```

8. **Crie uma página de login**

Da mesma forma, você pode criar uma página de login. No diretório `Pages`, crie um novo arquivo `Login.cshtml.cs` e adicione o seguinte código:

```csharp
using System.Threading.Tasks;
using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc;
using Microsoft.AspNetCore.Mvc.RazorPages;

namespace MyWebApp.Pages
{
    public class LoginModel : PageModel
    {
        private readonly SignInManager<IdentityUser> _signInManager;

        public LoginModel(SignInManager<IdentityUser> signInManager)
        {
            _signInManager = signInManager;
        }

        [BindProperty]
        public InputModel Input { get; set; }

        public class InputModel
        {
            public string Email { get; set; }
            public string Password { get; set; }
        }

        public async Task<IActionResult> OnPostAsync()
        {
            if (ModelState.IsValid)
            {
                var result = await _signInManager.PasswordSignInAsync(Input.Email, Input.Password, isPersistent: false, lockoutOnFailure: false);
                if (result.Succeeded)
                {
                    return RedirectToPage("/Index");
                }
                else
                {
                    ModelState.AddModelError(string.Empty, "Invalid login attempt.");
                    return Page();
                }
            }
            return Page();
        }
    }
}
```

E crie um arquivo `Login.cshtml` com o seguinte código:

```html
@page
@model LoginModel
<form method="post">
    <input asp-for="Input.Email" type="email" placeholder="Email" />
    <input asp-for="Input.Password" type="password" placeholder="Password" />
    <button type="submit">Login</button>
</form>
```

9. **Execute o projeto**

Finalmente, você pode executar o projeto com o seguinte comando:

```bash
dotnet run
```

Este exemplo usa o ASP.NET Core Identity para gerenciar usuários e autenticação, e o Entity Framework Core para gerenciar o banco de dados. As páginas de registro e login são criadas usando o Razor Pages.