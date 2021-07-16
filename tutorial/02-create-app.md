---
ms.openlocfilehash: 4c021fe8aac9b42ee0984a15e73366ead847ee06
ms.sourcegitcommit: ef990e983274cb161bfe16a8dff801d30a798f04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2021
ms.locfileid: "53446979"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="a6d3d-101">Начните с создания приложения Blazor WebAssembly.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-101">Start by creating a Blazor WebAssembly app.</span></span>

1. <span data-ttu-id="a6d3d-102">Откройте интерфейс командной строки (CLI) в каталоге, в котором необходимо создать проект.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-102">Open your command-line interface (CLI) in a directory where you want to create the project.</span></span> <span data-ttu-id="a6d3d-103">Выполните следующую команду.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-103">Run the following command.</span></span>

    ```Shell
    dotnet new blazorwasm --auth SingleOrg -o GraphTutorial
    ```

    <span data-ttu-id="a6d3d-104">Этот параметр заставляет созданный проект включать конфигурацию для проверки подлинности `--auth SingleOrg` с помощью платформа удостоверений Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-104">The `--auth SingleOrg` parameter causes the generated project to include configuration for authentication with the Microsoft identity platform.</span></span>

1. <span data-ttu-id="a6d3d-105">После создания проекта убедитесь, что он работает путем изменения текущего каталога в **каталог GraphTutorial** и запуска следующей команды в CLI.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-105">Once the project is created, verify that it works by changing the current directory to the **GraphTutorial** directory and running the following command in your CLI.</span></span>

    ```Shell
    dotnet watch run
    ```

1. <span data-ttu-id="a6d3d-106">Откройте браузер и просмотрите `https://localhost:5001` .</span><span class="sxs-lookup"><span data-stu-id="a6d3d-106">Open your browser and browse to `https://localhost:5001`.</span></span> <span data-ttu-id="a6d3d-107">Если все работает, вы должны увидеть "Привет, мир!"</span><span class="sxs-lookup"><span data-stu-id="a6d3d-107">If everything is working, you should see a "Hello, world!"</span></span> <span data-ttu-id="a6d3d-108">Сообщение.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-108">message.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a6d3d-109">Если вы получаете предупреждение о том, что сертификат **localhost** не доверяется, вы можете использовать CLI core .NET для установки сертификата разработки и доверия к этому сертификату.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-109">If you receive a warning that the certificate for **localhost** is un-trusted you can use the .NET Core CLI to install and trust the development certificate.</span></span> <span data-ttu-id="a6d3d-110">Инструкции по конкретным [операционным системам см. в ASP.NET Core https.ru.](/aspnet/core/security/enforcing-ssl)</span><span class="sxs-lookup"><span data-stu-id="a6d3d-110">See [Enforce HTTPS in ASP.NET Core](/aspnet/core/security/enforcing-ssl) for instructions for specific operating systems.</span></span>

## <a name="add-nuget-packages"></a><span data-ttu-id="a6d3d-111">Добавление пакетов NuGet</span><span class="sxs-lookup"><span data-stu-id="a6d3d-111">Add NuGet packages</span></span>

<span data-ttu-id="a6d3d-112">Прежде чем двигаться дальше, установите дополнительные NuGet пакеты, которые вы будете использовать позже.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-112">Before moving on, install some additional NuGet packages that you will use later.</span></span>

- <span data-ttu-id="a6d3d-113">[Microsoft.Graph](https://www.nuget.org/packages/Microsoft.Graph/) для вызовов Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-113">[Microsoft.Graph](https://www.nuget.org/packages/Microsoft.Graph/) for making calls to Microsoft Graph.</span></span>
- <span data-ttu-id="a6d3d-114">[TimeZoneConverter](https://github.com/mj1856/TimeZoneConverter) для перевода Windows идентификаторов часовой зоны в идентификаторы IANA.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-114">[TimeZoneConverter](https://github.com/mj1856/TimeZoneConverter) for translating Windows time zone identifiers to IANA identifiers.</span></span>

1. <span data-ttu-id="a6d3d-115">Запустите следующие команды в CLI для установки зависимостей.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-115">Run the following commands in your CLI to install the dependencies.</span></span>

    ```Shell
    dotnet add package Microsoft.Graph --version 4.0.0
    dotnet add package TimeZoneConverter
    ```

## <a name="design-the-app"></a><span data-ttu-id="a6d3d-116">Проектирование приложения</span><span class="sxs-lookup"><span data-stu-id="a6d3d-116">Design the app</span></span>

<span data-ttu-id="a6d3d-117">В этом разделе будет создаваться базовая структура пользовательского интерфейса приложения.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-117">In this section you will create the basic UI structure of the application.</span></span>

1. <span data-ttu-id="a6d3d-118">Удалите примеры страниц, созданных шаблоном.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-118">Remove sample pages generated by the template.</span></span> <span data-ttu-id="a6d3d-119">Удаление следующих файлов.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-119">Delete the following files.</span></span>

    - <span data-ttu-id="a6d3d-120">**./Pages/Counter.razor**</span><span class="sxs-lookup"><span data-stu-id="a6d3d-120">**./Pages/Counter.razor**</span></span>
    - <span data-ttu-id="a6d3d-121">**./Pages/FetchData.razor**</span><span class="sxs-lookup"><span data-stu-id="a6d3d-121">**./Pages/FetchData.razor**</span></span>
    - <span data-ttu-id="a6d3d-122">**./Shared/SurveyPrompt.razor**</span><span class="sxs-lookup"><span data-stu-id="a6d3d-122">**./Shared/SurveyPrompt.razor**</span></span>
    - <span data-ttu-id="a6d3d-123">**./wwwroot/sample-data/weather.json**</span><span class="sxs-lookup"><span data-stu-id="a6d3d-123">**./wwwroot/sample-data/weather.json**</span></span>

1. <span data-ttu-id="a6d3d-124">Откройте **./wwwroot/index.html** и добавьте следующий код **перед** закрытием `</body>` тега.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-124">Open **./wwwroot/index.html** and add the following code just **before** the closing `</body>` tag.</span></span>

    :::code language="html" source="../demo/GraphTutorial/wwwroot/index.html" id="BootStrapJSSnippet":::

    <span data-ttu-id="a6d3d-125">Это добавляет [файлы javascript Bootstrap.](https://getbootstrap.com/docs/4.5/getting-started/introduction/)</span><span class="sxs-lookup"><span data-stu-id="a6d3d-125">This adds the [Bootstrap](https://getbootstrap.com/docs/4.5/getting-started/introduction/) javascript files.</span></span>

1. <span data-ttu-id="a6d3d-126">Откройте **./wwwroot/css/app.css** и добавьте следующий код.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-126">Open **./wwwroot/css/app.css** and add the following code.</span></span>

    :::code language="css" source="../demo/GraphTutorial/wwwroot/css/app.css" id="CssSnippet":::

1. <span data-ttu-id="a6d3d-127">Откройте **./Shared/NavMenu.razor** и замените его содержимое следующим.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-127">Open **./Shared/NavMenu.razor** and replace its contents with the following.</span></span>

    :::code language="razor" source="../demo/GraphTutorial/Shared/NavMenu.razor" id="NavMenuSnippet":::

1. <span data-ttu-id="a6d3d-128">Откройте **./Pages/Index.razor** и замените его содержимое следующим.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-128">Open **./Pages/Index.razor** and replace its contents with the following.</span></span>

    :::code language="razor" source="../demo/GraphTutorial/Pages/Index.razor" id="IndexSnippet":::

1. <span data-ttu-id="a6d3d-129">Откройте **./Shared/LoginDisplay.razor** и замените содержимое на следующее.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-129">Open **./Shared/LoginDisplay.razor** and replace its contents with the following.</span></span>

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

1. <span data-ttu-id="a6d3d-130">Создайте новый каталог в **каталоге ./wwwroot** с именем **img**.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-130">Create a new directory in the **./wwwroot** directory named **img**.</span></span> <span data-ttu-id="a6d3d-131">Добавьте файл изображений выбора с именем **no-profile-photo.png** в этом каталоге.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-131">Add an image file of your choosing named **no-profile-photo.png** in this directory.</span></span> <span data-ttu-id="a6d3d-132">Это изображение будет использоваться в качестве фотографии пользователя, если у пользователя нет фотографии в Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-132">This image will be used as the user's photo when the user has no photo in Microsoft Graph.</span></span>

    > [!TIP]
    > <span data-ttu-id="a6d3d-133">Вы можете скачать изображение, используемую на этих скриншотах из [GitHub](https://github.com/microsoftgraph/msgraph-training-blazor-clientside/blob/master/demo/GraphTutorial/wwwroot/img/no-profile-photo.png).</span><span class="sxs-lookup"><span data-stu-id="a6d3d-133">You can download the image used in these screenshots from [GitHub](https://github.com/microsoftgraph/msgraph-training-blazor-clientside/blob/master/demo/GraphTutorial/wwwroot/img/no-profile-photo.png).</span></span>

1. <span data-ttu-id="a6d3d-134">Сохраните все изменения и обновите страницу.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-134">Save all of your changes and refresh the page.</span></span>

    ![Снимок экрана: обновленная домашняя страница](./images/create-app-01.png)
