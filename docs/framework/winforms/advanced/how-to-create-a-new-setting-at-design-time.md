---
title: "Comment : créer un nouveau paramètre au moment du design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e8a05b6f37f7686f18a6200e009aabe7eed5537
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="96501-102">Comment : créer un nouveau paramètre au moment du design</span><span class="sxs-lookup"><span data-stu-id="96501-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="96501-103">Vous pouvez créer un nouveau paramètre au moment du design à l’aide du Concepteur de paramètres.</span><span class="sxs-lookup"><span data-stu-id="96501-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="96501-104">Le Concepteur de paramètres est une interface de style de la grille qui vous permet de créer de nouveaux paramètres et de spécifier des propriétés pour ces paramètres.</span><span class="sxs-lookup"><span data-stu-id="96501-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="96501-105">Vous devez spécifier le nom, valeur, Type et la portée de vos nouveaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="96501-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="96501-106">Une fois qu’un paramètre est créé, il est accessible dans le code.</span><span class="sxs-lookup"><span data-stu-id="96501-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="96501-107">Pour créer un nouveau paramètre au moment du design en c#</span><span class="sxs-lookup"><span data-stu-id="96501-107">To create a new setting at design time in C#</span></span>  
  
1.  <span data-ttu-id="96501-108">Dans **l’Explorateur de solutions**, développez le **propriétés** nœud de votre projet.</span><span class="sxs-lookup"><span data-stu-id="96501-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="96501-109">Double-cliquez sur le fichier .settings dans lequel vous souhaitez ajouter un nouveau paramètre.</span><span class="sxs-lookup"><span data-stu-id="96501-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="96501-110">Le nom par défaut pour ce fichier est Settings.settings.</span><span class="sxs-lookup"><span data-stu-id="96501-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="96501-111">Dans le Concepteur de paramètres, définissez le nom de valeur, Type et portée de votre paramètre.</span><span class="sxs-lookup"><span data-stu-id="96501-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="96501-112">Chaque ligne représente un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="96501-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="96501-113">Pour créer un nouveau paramètre au moment du design dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="96501-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="96501-114">Dans **l’Explorateur de solutions**, cliquez sur le nœud de votre projet et choisissez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="96501-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="96501-115">Dans le **propriétés** page, sélectionnez le **paramètres** onglet.</span><span class="sxs-lookup"><span data-stu-id="96501-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="96501-116">Dans le Concepteur de paramètres, définissez le nom de valeur, Type et portée de votre paramètre.</span><span class="sxs-lookup"><span data-stu-id="96501-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="96501-117">Chaque ligne représente un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="96501-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96501-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96501-118">See Also</span></span>  
 [<span data-ttu-id="96501-119">Utilisation de paramètres d'application et de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="96501-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="96501-120">Vue d'ensemble des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="96501-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="96501-121">Guide pratique pour modifier la valeur d'un paramètre existant au moment du design</span><span class="sxs-lookup"><span data-stu-id="96501-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
