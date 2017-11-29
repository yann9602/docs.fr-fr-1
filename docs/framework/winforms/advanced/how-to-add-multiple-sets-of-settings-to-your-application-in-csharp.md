---
title: "Comment : ajouter plusieurs jeux de paramètres à votre application en C#"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec541a8f83990eec79226be7fb4880ef8dda639d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a><span data-ttu-id="e6540-102">Comment : ajouter plusieurs jeux de paramètres à votre application en C#</span><span class="sxs-lookup"><span data-stu-id="e6540-102">How To: Add Multiple Sets of Settings To Your Application in C#</span></span> #
<span data-ttu-id="e6540-103">Dans certains cas, vous souhaiterez ont plusieurs ensembles de paramètres dans une application.</span><span class="sxs-lookup"><span data-stu-id="e6540-103">In some cases, you might want to have multiple sets of settings in an application.</span></span> <span data-ttu-id="e6540-104">Par exemple, si vous développez une application où un groupe particulier de paramètres est supposé changer fréquemment, il peut être judicieux de les placer dans un fichier unique afin que le fichier peut être remplacé en gros, sans affecter les autres paramètres.</span><span class="sxs-lookup"><span data-stu-id="e6540-104">For example, if you are developing an application where a particular group of settings is expected to change frequently, it might be wise to separate them all into a single file so that the file can be replaced wholesale, leaving other settings unaffected.</span></span> <span data-ttu-id="e6540-105">Visual Studio vous permet de vous permet d’ajouter plusieurs jeux de paramètres à votre projet.</span><span class="sxs-lookup"><span data-stu-id="e6540-105">Visual Studio allows you to add multiple sets of settings to your project.</span></span> <span data-ttu-id="e6540-106">Jeux de paramètres supplémentaires sont accessibles via l’objet Properties.Settings.</span><span class="sxs-lookup"><span data-stu-id="e6540-106">Additional sets of settings can be accessed via the Properties.Settings object.</span></span>  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a><span data-ttu-id="e6540-107">Pour ajouter un jeu supplémentaire de paramètres à votre Application</span><span class="sxs-lookup"><span data-stu-id="e6540-107">To Add an Additional Set of Setting to your Application</span></span>  
  
1.  <span data-ttu-id="e6540-108">Dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="e6540-108">From the **Project** menu, choose **Add New Item**.</span></span> <span data-ttu-id="e6540-109">La boîte de dialogue **Ajouter un nouvel élément** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="e6540-109">The **Add New Item** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="e6540-110">Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **fichier de paramètres**, tapez un nom pour le fichier, puis cliquez sur **ajouter** pour ajouter un nouveau fichier de paramètres à votre solution.</span><span class="sxs-lookup"><span data-stu-id="e6540-110">In the **Add New Item** dialog box, select **Settings File**, type in a name for the file, and click **Add** to add a new settings file to your solution.</span></span>  
  
3.  <span data-ttu-id="e6540-111">Dans **l’Explorateur de solutions**, faites glisser le nouveau fichier de paramètres dans le **propriétés** dossier.</span><span class="sxs-lookup"><span data-stu-id="e6540-111">In **Solution Explorer**, drag the new Settings file into the **Properties** folder.</span></span> <span data-ttu-id="e6540-112">Ainsi, vos nouveaux paramètres soient disponibles dans le code.</span><span class="sxs-lookup"><span data-stu-id="e6540-112">This allows your new settings to be available in code.</span></span>  
  
4.  <span data-ttu-id="e6540-113">Ajouter et utiliser des paramètres de ce fichier comme vous le feriez pour tout autre fichier de paramètres.</span><span class="sxs-lookup"><span data-stu-id="e6540-113">Add and use settings in this file as you would any other settings file.</span></span> <span data-ttu-id="e6540-114">Vous pouvez accéder à ce groupe de paramètres via l’objet Properties.Settings.</span><span class="sxs-lookup"><span data-stu-id="e6540-114">You can access this group of settings via the Properties.Settings object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6540-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6540-115">See Also</span></span>  
 [<span data-ttu-id="e6540-116">Utilisation de paramètres d'application et de paramètres utilisateur</span><span class="sxs-lookup"><span data-stu-id="e6540-116">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="e6540-117">Vue d'ensemble des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="e6540-117">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
