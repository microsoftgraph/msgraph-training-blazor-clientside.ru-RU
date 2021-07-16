---
ms.openlocfilehash: c9fb7269969b0ef4e0300b8884c3ed168216b6cc
ms.sourcegitcommit: ef990e983274cb161bfe16a8dff801d30a798f04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2021
ms.locfileid: "53446968"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="9335e-101">В этом упражнении будет создаваться новая регистрация веб-приложений Azure AD с помощью центра администрирования Azure Active Directory администратора.</span><span class="sxs-lookup"><span data-stu-id="9335e-101">In this exercise, you will create a new Azure AD web application registration using the Azure Active Directory admin center.</span></span>

1. <span data-ttu-id="9335e-102">Откройте браузер и перейдите в [Центр администрирования Azure Active Directory](https://aad.portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="9335e-102">Open a browser and navigate to the [Azure Active Directory admin center](https://aad.portal.azure.com).</span></span> <span data-ttu-id="9335e-103">Войдите с помощью **личной учетной записи** (т.е. учетной записи Microsoft) или **рабочей (учебной) учетной записи**.</span><span class="sxs-lookup"><span data-stu-id="9335e-103">Login using a **personal account** (aka: Microsoft Account) or **Work or School Account**.</span></span>

1. <span data-ttu-id="9335e-104">Выберите **Azure Active Directory** на панели навигации слева, затем выберите **Регистрация приложений** в разделе **Управление**.</span><span class="sxs-lookup"><span data-stu-id="9335e-104">Select **Azure Active Directory** in the left-hand navigation, then select **App registrations** under **Manage**.</span></span>

    ![<span data-ttu-id="9335e-105">Снимок экрана регистрации приложения</span><span class="sxs-lookup"><span data-stu-id="9335e-105">A screenshot of the App registrations</span></span> ](./images/aad-portal-app-registrations.png)

1. <span data-ttu-id="9335e-106">Выберите **Новая регистрация**.</span><span class="sxs-lookup"><span data-stu-id="9335e-106">Select **New registration**.</span></span> <span data-ttu-id="9335e-107">На странице **Зарегистрировать приложение** задайте необходимые значения следующим образом.</span><span class="sxs-lookup"><span data-stu-id="9335e-107">On the **Register an application** page, set the values as follows.</span></span>

    - <span data-ttu-id="9335e-108">Введите **имя** `Blazor Graph Tutorial`.</span><span class="sxs-lookup"><span data-stu-id="9335e-108">Set **Name** to `Blazor Graph Tutorial`.</span></span>
    - <span data-ttu-id="9335e-109">Введите **поддерживаемые типы учетных записей** для **учетных записей в любом каталоге организаций и личных учетных записей Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="9335e-109">Set **Supported account types** to **Accounts in any organizational directory and personal Microsoft accounts**.</span></span>
    - <span data-ttu-id="9335e-110">В **статье Перенаправление URI** установите первое падение в одно-страницу приложения **(SPA)** и установите значение `https://localhost:5001/authentication/login-callback` .</span><span class="sxs-lookup"><span data-stu-id="9335e-110">Under **Redirect URI**, set the first drop-down to **Single-page application (SPA)** and set the value to `https://localhost:5001/authentication/login-callback`.</span></span>

    ![Снимок экрана со страницей регистрации приложения](./images/aad-register-an-app.png)

1. <span data-ttu-id="9335e-112">Нажмите **Зарегистрировать**.</span><span class="sxs-lookup"><span data-stu-id="9335e-112">Select **Register**.</span></span> <span data-ttu-id="9335e-113">На странице **Учебник Graph Blazor скопируйте** значение ID приложения **(клиента)** и сохраните его, оно потребуется на следующем шаге.</span><span class="sxs-lookup"><span data-stu-id="9335e-113">On the **Blazor Graph Tutorial** page, copy the value of the **Application (client) ID** and save it, you will need it in the next step.</span></span>

    ![Снимок экрана с идентификатором приложения для новой регистрации](./images/aad-application-id.png)
