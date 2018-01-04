---
title: "Utilisation de paramètres d'application et de paramètres utilisateur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user settings [Windows Forms]
- application settings [Windows Forms], how-to topics
ms.assetid: 54682d3b-1cbf-4683-9351-012b8b4286b5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 310fcad07ce7cf541312ff83e41d7e5fc2643898
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-application-settings-and-user-settings"></a><span data-ttu-id="9f45d-102">Utilisation de paramètres d'application et de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="9f45d-102">Using Application Settings and User Settings</span></span>
<span data-ttu-id="9f45d-103">À compter de .NET Framework 2.0, vous pouvez créer et accéder aux valeurs qui sont conservées entre les sessions d’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="9f45d-103">Starting with the .NET Framework 2.0, you can create and access values that are persisted between application execution sessions.</span></span> <span data-ttu-id="9f45d-104">Ces valeurs sont appelées *paramètres*.</span><span class="sxs-lookup"><span data-stu-id="9f45d-104">These values are called *settings*.</span></span> <span data-ttu-id="9f45d-105">Les paramètres peuvent représenter des préférences de l’utilisateur ou des informations précieuses l’application doivent utiliser.</span><span class="sxs-lookup"><span data-stu-id="9f45d-105">Settings can represent user preferences, or valuable information the application needs to use.</span></span> <span data-ttu-id="9f45d-106">Par exemple, vous pouvez créer une série de paramètres qui stockent les préférences utilisateur pour le jeu de couleurs d’une application.</span><span class="sxs-lookup"><span data-stu-id="9f45d-106">For example, you might create a series of settings that store user preferences for the color scheme of an application.</span></span> <span data-ttu-id="9f45d-107">Ou bien, vous pouvez stocker la chaîne de connexion qui spécifie une base de données utilisées par votre application.</span><span class="sxs-lookup"><span data-stu-id="9f45d-107">Or you might store the connection string that specifies a database that your application uses.</span></span> <span data-ttu-id="9f45d-108">Les paramètres permettent de que vous permettent de conserver les informations qui sont essentielles à l’application en dehors du code et pour créer des profils qui stockent les préférences des utilisateurs individuels.</span><span class="sxs-lookup"><span data-stu-id="9f45d-108">Settings allow you to both persist information that is critical to the application outside the code, and to create profiles that store the preferences of individual users.</span></span>  
  
 <span data-ttu-id="9f45d-109">Les rubriques de cette section décrivent comment utiliser des paramètres au moment du design et la durée d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9f45d-109">The topics in this section describe how to use settings at design time and run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9f45d-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9f45d-110">In This Section</span></span>  
 [<span data-ttu-id="9f45d-111">Guide pratique pour créer un nouveau paramètre au moment du design</span><span class="sxs-lookup"><span data-stu-id="9f45d-111">How To: Create a New Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)  
  
 <span data-ttu-id="9f45d-112">Explique comment utiliser Visual Studio pour créer un nouveau paramètre pour une application.</span><span class="sxs-lookup"><span data-stu-id="9f45d-112">Explains how to use Visual Studio to create a new setting for an application.</span></span>  
  
 [<span data-ttu-id="9f45d-113">Guide pratique pour modifier la valeur d'un paramètre existant au moment du design</span><span class="sxs-lookup"><span data-stu-id="9f45d-113">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)  
  
 <span data-ttu-id="9f45d-114">Décrit comment utiliser Visual Studio pour modifier la valeur d’un paramètre existant.</span><span class="sxs-lookup"><span data-stu-id="9f45d-114">Describes how to use Visual Studio to change the value of an existing setting.</span></span>  
  
 [<span data-ttu-id="9f45d-115">Guide pratique pour modifier la valeur d'un paramètre entre des sessions d'application</span><span class="sxs-lookup"><span data-stu-id="9f45d-115">How To: Change the Value of a Setting Between Application Sessions</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-a-setting-between-application-sessions.md)  
  
 <span data-ttu-id="9f45d-116">Explique comment modifier la valeur d’un paramètre dans une application compilée entre des sessions d’application.</span><span class="sxs-lookup"><span data-stu-id="9f45d-116">Details how to change the value of a setting in a compiled application between application sessions.</span></span>  
  
 [<span data-ttu-id="9f45d-117">Guide pratique pour lire des paramètres au moment de l'exécution avec C#</span><span class="sxs-lookup"><span data-stu-id="9f45d-117">How To: Read Settings at Run Time With C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="9f45d-118">Décrit comment utiliser le code pour lire des paramètres avec c#.</span><span class="sxs-lookup"><span data-stu-id="9f45d-118">Describes how to use code to read settings with C#.</span></span>  
  
 [<span data-ttu-id="9f45d-119">Guide pratique pour écrire des paramètres utilisateur au moment de l'exécution avec C#</span><span class="sxs-lookup"><span data-stu-id="9f45d-119">How To: Write User Settings at Run Time with C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)  
  
 <span data-ttu-id="9f45d-120">Explique comment utiliser du code pour écrire et enregistrer les valeurs des paramètres de l’utilisateur avec c#.</span><span class="sxs-lookup"><span data-stu-id="9f45d-120">Explains how to use code to write and save the values of user settings with C#.</span></span>  
  
 [<span data-ttu-id="9f45d-121">Guide pratique pour ajouter plusieurs jeux de paramètres à votre application en C#</span><span class="sxs-lookup"><span data-stu-id="9f45d-121">How To: Add Multiple Sets of Settings To Your Application in C#</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-multiple-sets-of-settings-to-your-application-in-csharp.md)  
  
 <span data-ttu-id="9f45d-122">Explique comment ajouter plusieurs jeux de paramètres à une application avec c#.</span><span class="sxs-lookup"><span data-stu-id="9f45d-122">Details how to add multiple sets of settings to an application with C#.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f45d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f45d-123">See Also</span></span>  
 [<span data-ttu-id="9f45d-124">Paramètres d'application pour les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f45d-124">Application Settings for Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/application-settings-for-windows-forms.md)
