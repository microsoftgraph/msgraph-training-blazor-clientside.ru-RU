---
ms.openlocfilehash: 25caea9275c57faa9c741e274ac90606959422c2
ms.sourcegitcommit: ef990e983274cb161bfe16a8dff801d30a798f04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2021
ms.locfileid: "53446986"
---
<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="53b90-101">В этом руководстве рассказывается о создании клиентского приложения Blazor WebAssembly, которое использует API microsoft Graph для получения данных календаря для пользователя.</span><span class="sxs-lookup"><span data-stu-id="53b90-101">This tutorial teaches you how to build a client-side Blazor WebAssembly app that uses the Microsoft Graph API to retrieve calendar information for a user.</span></span>

> [!TIP]
> <span data-ttu-id="53b90-102">Если вы предпочитаете просто скачать завершенный учебник, вы можете скачать или клонировать [GitHub репозиторий](https://github.com/microsoftgraph/msgraph-training-blazor-clientside).</span><span class="sxs-lookup"><span data-stu-id="53b90-102">If you prefer to just download the completed tutorial, you can download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-blazor-clientside).</span></span> <span data-ttu-id="53b90-103">Инструкции по настройке  приложения с помощью ID-приложения и секрета см. в файле README в демо-папке.</span><span class="sxs-lookup"><span data-stu-id="53b90-103">See the README file in the **demo** folder for instructions on configuring the app with an app ID and secret.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="53b90-104">Предварительные требования</span><span class="sxs-lookup"><span data-stu-id="53b90-104">Prerequisites</span></span>

<span data-ttu-id="53b90-105">Прежде чем приступить к этому учебнику, необходимо установить [SDK.NET Core на](https://dotnet.microsoft.com/download) компьютере разработки.</span><span class="sxs-lookup"><span data-stu-id="53b90-105">Before you start this tutorial, you should have the [.NET Core SDK](https://dotnet.microsoft.com/download) installed on your development machine.</span></span> <span data-ttu-id="53b90-106">Если у вас нет SDK, посетите предыдущую ссылку для скачать параметры.</span><span class="sxs-lookup"><span data-stu-id="53b90-106">If you do not have the SDK, visit the previous link for download options.</span></span>

<span data-ttu-id="53b90-107">Вы также должны иметь личную учетную запись Майкрософт с почтовым ящиком на Outlook.com или учетную запись Microsoft work или school.</span><span class="sxs-lookup"><span data-stu-id="53b90-107">You should also have either a personal Microsoft account with a mailbox on Outlook.com, or a Microsoft work or school account.</span></span> <span data-ttu-id="53b90-108">Если у вас нет учетной записи Майкрософт, существует несколько вариантов получения бесплатной учетной записи:</span><span class="sxs-lookup"><span data-stu-id="53b90-108">If you don't have a Microsoft account, there are a couple of options to get a free account:</span></span>

- <span data-ttu-id="53b90-109">Вы можете [зарегистрироваться для новой личной учетной записи Майкрософт.](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=12&ct=1454618383&rver=6.4.6456.0&wp=MBI_SSL_SHARED&wreply=https://mail.live.com/default.aspx&id=64855&cbcxt=mai&bk=1454618383&uiflavor=web&uaid=b213a65b4fdc484382b6622b3ecaa547&mkt=E-US&lc=1033&lic=1)</span><span class="sxs-lookup"><span data-stu-id="53b90-109">You can [sign up for a new personal Microsoft account](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=12&ct=1454618383&rver=6.4.6456.0&wp=MBI_SSL_SHARED&wreply=https://mail.live.com/default.aspx&id=64855&cbcxt=mai&bk=1454618383&uiflavor=web&uaid=b213a65b4fdc484382b6622b3ecaa547&mkt=E-US&lc=1033&lic=1).</span></span>
- <span data-ttu-id="53b90-110">Вы можете [зарегистрироваться в программе Office 365 разработчика,](https://developer.microsoft.com/office/dev-program) чтобы получить бесплатную Office 365 подписку.</span><span class="sxs-lookup"><span data-stu-id="53b90-110">You can [sign up for the Office 365 Developer Program](https://developer.microsoft.com/office/dev-program) to get a free Office 365 subscription.</span></span>

> [!NOTE]
> <span data-ttu-id="53b90-111">Это руководство было написано с .NET Core SDK версии 5.0.302.</span><span class="sxs-lookup"><span data-stu-id="53b90-111">This tutorial was written with .NET Core SDK version 5.0.302.</span></span> <span data-ttu-id="53b90-112">Действия в этом руководстве могут работать с другими версиями, но они не были проверены.</span><span class="sxs-lookup"><span data-stu-id="53b90-112">The steps in this guide may work with other versions, but that has not been tested.</span></span>

## <a name="feedback"></a><span data-ttu-id="53b90-113">Отзывы</span><span class="sxs-lookup"><span data-stu-id="53b90-113">Feedback</span></span>

<span data-ttu-id="53b90-114">В репозитории [](https://github.com/microsoftgraph/msgraph-training-blazor-clientside)GitHub.</span><span class="sxs-lookup"><span data-stu-id="53b90-114">Please provide any feedback on this tutorial in the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-blazor-clientside).</span></span>
