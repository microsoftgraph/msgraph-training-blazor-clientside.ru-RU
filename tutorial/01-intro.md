---
ms.openlocfilehash: 25caea9275c57faa9c741e274ac90606959422c2
ms.sourcegitcommit: ef990e983274cb161bfe16a8dff801d30a798f04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2021
ms.locfileid: "53446986"
---
<!-- markdownlint-disable MD002 MD041 -->

В этом руководстве рассказывается о создании клиентского приложения Blazor WebAssembly, которое использует API microsoft Graph для получения данных календаря для пользователя.

> [!TIP]
> Если вы предпочитаете просто скачать завершенный учебник, вы можете скачать или клонировать [GitHub репозиторий](https://github.com/microsoftgraph/msgraph-training-blazor-clientside). Инструкции по настройке  приложения с помощью ID-приложения и секрета см. в файле README в демо-папке.

## <a name="prerequisites"></a>Предварительные требования

Прежде чем приступить к этому учебнику, необходимо установить [SDK.NET Core на](https://dotnet.microsoft.com/download) компьютере разработки. Если у вас нет SDK, посетите предыдущую ссылку для скачать параметры.

Вы также должны иметь личную учетную запись Майкрософт с почтовым ящиком на Outlook.com или учетную запись Microsoft work или school. Если у вас нет учетной записи Майкрософт, существует несколько вариантов получения бесплатной учетной записи:

- Вы можете [зарегистрироваться для новой личной учетной записи Майкрософт.](https://signup.live.com/signup?wa=wsignin1.0&rpsnv=12&ct=1454618383&rver=6.4.6456.0&wp=MBI_SSL_SHARED&wreply=https://mail.live.com/default.aspx&id=64855&cbcxt=mai&bk=1454618383&uiflavor=web&uaid=b213a65b4fdc484382b6622b3ecaa547&mkt=E-US&lc=1033&lic=1)
- Вы можете [зарегистрироваться в программе Office 365 разработчика,](https://developer.microsoft.com/office/dev-program) чтобы получить бесплатную Office 365 подписку.

> [!NOTE]
> Это руководство было написано с .NET Core SDK версии 5.0.302. Действия в этом руководстве могут работать с другими версиями, но они не были проверены.

## <a name="feedback"></a>Отзывы

В репозитории [](https://github.com/microsoftgraph/msgraph-training-blazor-clientside)GitHub.
