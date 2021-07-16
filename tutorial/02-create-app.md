---
ms.openlocfilehash: 4c021fe8aac9b42ee0984a15e73366ead847ee06
ms.sourcegitcommit: ef990e983274cb161bfe16a8dff801d30a798f04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2021
ms.locfileid: "53446979"
---
<!-- markdownlint-disable MD002 MD041 -->

Начните с создания приложения Blazor WebAssembly.

1. Откройте интерфейс командной строки (CLI) в каталоге, в котором необходимо создать проект. Выполните следующую команду.

    ```Shell
    dotnet new blazorwasm --auth SingleOrg -o GraphTutorial
    ```

    Этот параметр заставляет созданный проект включать конфигурацию для проверки подлинности `--auth SingleOrg` с помощью платформа удостоверений Майкрософт.

1. После создания проекта убедитесь, что он работает путем изменения текущего каталога в **каталог GraphTutorial** и запуска следующей команды в CLI.

    ```Shell
    dotnet watch run
    ```

1. Откройте браузер и просмотрите `https://localhost:5001` . Если все работает, вы должны увидеть "Привет, мир!" Сообщение.

> [!IMPORTANT]
> Если вы получаете предупреждение о том, что сертификат **localhost** не доверяется, вы можете использовать CLI core .NET для установки сертификата разработки и доверия к этому сертификату. Инструкции по конкретным [операционным системам см. в ASP.NET Core https.ru.](/aspnet/core/security/enforcing-ssl)

## <a name="add-nuget-packages"></a>Добавление пакетов NuGet

Прежде чем двигаться дальше, установите дополнительные NuGet пакеты, которые вы будете использовать позже.

- [Microsoft.Graph](https://www.nuget.org/packages/Microsoft.Graph/) для вызовов Microsoft Graph.
- [TimeZoneConverter](https://github.com/mj1856/TimeZoneConverter) для перевода Windows идентификаторов часовой зоны в идентификаторы IANA.

1. Запустите следующие команды в CLI для установки зависимостей.

    ```Shell
    dotnet add package Microsoft.Graph --version 4.0.0
    dotnet add package TimeZoneConverter
    ```

## <a name="design-the-app"></a>Проектирование приложения

В этом разделе будет создаваться базовая структура пользовательского интерфейса приложения.

1. Удалите примеры страниц, созданных шаблоном. Удаление следующих файлов.

    - **./Pages/Counter.razor**
    - **./Pages/FetchData.razor**
    - **./Shared/SurveyPrompt.razor**
    - **./wwwroot/sample-data/weather.json**

1. Откройте **./wwwroot/index.html** и добавьте следующий код **перед** закрытием `</body>` тега.

    :::code language="html" source="../demo/GraphTutorial/wwwroot/index.html" id="BootStrapJSSnippet":::

    Это добавляет [файлы javascript Bootstrap.](https://getbootstrap.com/docs/4.5/getting-started/introduction/)

1. Откройте **./wwwroot/css/app.css** и добавьте следующий код.

    :::code language="css" source="../demo/GraphTutorial/wwwroot/css/app.css" id="CssSnippet":::

1. Откройте **./Shared/NavMenu.razor** и замените его содержимое следующим.

    :::code language="razor" source="../demo/GraphTutorial/Shared/NavMenu.razor" id="NavMenuSnippet":::

1. Откройте **./Pages/Index.razor** и замените его содержимое следующим.

    :::code language="razor" source="../demo/GraphTutorial/Pages/Index.razor" id="IndexSnippet":::

1. Откройте **./Shared/LoginDisplay.razor** и замените содержимое на следующее.

    ```razor
    @using Microsoft.AspNetCore.Components.Authorization
    @using Microsoft.AspNetCore.Components.WebAssembly.Authentication

    @inject NavigationManager Navigation
    @inject SignOutSessionStateManager SignOutManager

    <AuthorizeView>
        <Authorized>
            <a class="text-decoration-none" data-toggle="dropdown" href="#" role="button">
                <img src="/img/no-profile-photo.png" class="nav-profile-photo rounded-circle align-self-center mr-2">
            </a>
            <div class="dropdown-menu dropdown-menu-right">
                <h5 class="dropdown-item-text mb-0">@context.User.Identity.Name</h5>
                <p class="dropdown-item-text text-muted mb-0">placeholder@contoso.com</p>
                <div class="dropdown-divider"></div>
                <button class="dropdown-item" @onclick="BeginLogout">Log out</button>
            </div>
        </Authorized>
        <NotAuthorized>
            <a href="authentication/login">Log in</a>
        </NotAuthorized>
    </AuthorizeView>

    @code{
        private async Task BeginLogout(MouseEventArgs args)
        {
            await SignOutManager.SetSignOutState();
            Navigation.NavigateTo("authentication/logout");
        }
    }
    ```

1. Создайте новый каталог в **каталоге ./wwwroot** с именем **img**. Добавьте файл изображений выбора с именем **no-profile-photo.png** в этом каталоге. Это изображение будет использоваться в качестве фотографии пользователя, если у пользователя нет фотографии в Microsoft Graph.

    > [!TIP]
    > Вы можете скачать изображение, используемую на этих скриншотах из [GitHub](https://github.com/microsoftgraph/msgraph-training-blazor-clientside/blob/master/demo/GraphTutorial/wwwroot/img/no-profile-photo.png).

1. Сохраните все изменения и обновите страницу.

    ![Снимок экрана: обновленная домашняя страница](./images/create-app-01.png)
