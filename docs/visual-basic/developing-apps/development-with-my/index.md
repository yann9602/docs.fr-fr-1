---
title: "Développement avec My (Visual Basic)"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.MyWpfExtension.Windows
dev_langs:
- VB
helpviewer_keywords:
- My object
- My namespace
- My feature
- Visual Basic, programming in
ms.assetid: f1d04509-5e46-4551-9f9f-94334a121fca
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3dae5e12baeb82c238381fb9e144c434816dcfb4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="development-with-my-visual-basic"></a><span data-ttu-id="aac9c-102">Développement avec My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aac9c-102">Development with My (Visual Basic)</span></span>
<span data-ttu-id="aac9c-103">Visual Basic propose de nouvelles fonctionnalités pour le développement rapide d’applications qui simplifient l’utilisation et améliorent la productivité tout en renforçant les performances.</span><span class="sxs-lookup"><span data-stu-id="aac9c-103">Visual Basic provides new features for rapid application development that improve productivity and ease of use while delivering power.</span></span> <span data-ttu-id="aac9c-104">Parmi ces nouvelles fonctionnalités, `My` permet d’accéder à des informations et des instances d’objet par défaut liées à l’application et à son environnement d’exécution.</span><span class="sxs-lookup"><span data-stu-id="aac9c-104">One of these features, called `My`, provides access to information and default object instances that are related to the application and its run-time environment.</span></span> <span data-ttu-id="aac9c-105">Ces informations sont organisées dans un format pouvant être découvert par IntelliSense et sont représentées logiquement, en fonction de l’utilisation.</span><span class="sxs-lookup"><span data-stu-id="aac9c-105">This information is organized in a format that is discoverable through IntelliSense and logically delineated according to use.</span></span>  
  
 <span data-ttu-id="aac9c-106">Les membres de niveau supérieur de `My` sont exposés en tant qu’objets.</span><span class="sxs-lookup"><span data-stu-id="aac9c-106">Top-level members of `My` are exposed as objects.</span></span> <span data-ttu-id="aac9c-107">Chaque objet se comporte comme un espace de noms ou une classe avec `Shared` membres et expose un ensemble de membres associés.</span><span class="sxs-lookup"><span data-stu-id="aac9c-107">Each object behaves similarly to a namespace or a class with `Shared` members, and it exposes a set of related members.</span></span>  
  
 <span data-ttu-id="aac9c-108">Ce tableau présente les objets `My` de niveau supérieur et leurs relations entre eux.</span><span class="sxs-lookup"><span data-stu-id="aac9c-108">This table shows the top-level `My` objects and their relationship to each other.</span></span>  
  
 <span data-ttu-id="aac9c-109">![Modèle objet pour My](../../../visual-basic/developing-apps/development-with-my/media/myobjmodel.gif "MyObjModel")</span><span class="sxs-lookup"><span data-stu-id="aac9c-109">![Object Model for My](../../../visual-basic/developing-apps/development-with-my/media/myobjmodel.gif "MyObjModel")</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aac9c-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="aac9c-110">In This Section</span></span>  
 [<span data-ttu-id="aac9c-111">Exécution de tâches avec My.Application, My.Computer et My.User</span><span class="sxs-lookup"><span data-stu-id="aac9c-111">Performing Tasks with My.Application, My.Computer, and My.User</span></span>](../../../visual-basic/developing-apps/development-with-my/performing-tasks-with-my-application-my-computer-and-my-user.md)  
 <span data-ttu-id="aac9c-112">Décrit les trois objets `My` centraux, `My.Application`, `My.Computer` et `My.User`, qui permettent d’accéder aux informations et aux fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="aac9c-112">Describes the three central `My` objects, `My.Application`, `My.Computer`, and `My.User`, which provide access to information and functionality</span></span>  
  
 [<span data-ttu-id="aac9c-113">Instances d’objets par défaut fournies par My.Forms et My.WebServices</span><span class="sxs-lookup"><span data-stu-id="aac9c-113">Default Object Instances Provided by My.Forms and My.WebServices</span></span>](../../../visual-basic/developing-apps/development-with-my/default-object-instances-provided-by-my-forms-and-my-webservices.md)  
 <span data-ttu-id="aac9c-114">Décrit les objets `My.Forms` et `My.WebServices` qui fournissent l’accès aux formulaires, sources de données et services Web XML utilisés par votre application.</span><span class="sxs-lookup"><span data-stu-id="aac9c-114">Describes the `My.Forms` and `My.WebServices` objects, which provide access to forms, data sources, and XML Web services used by your application.</span></span>  
  
 [<span data-ttu-id="aac9c-115">Développement rapide d’application avec My.Resources et My.Settings</span><span class="sxs-lookup"><span data-stu-id="aac9c-115">Rapid Application Development with My.Resources and My.Settings</span></span>](../../../visual-basic/developing-apps/development-with-my/rapid-application-development-with-my-resources-and-my-settings.md)  
 <span data-ttu-id="aac9c-116">Décrit les objets `My.Resources` et `My.Settings`, qui fournissent l’accès aux ressources et aux paramètres d’une application.</span><span class="sxs-lookup"><span data-stu-id="aac9c-116">Describes the `My.Resources` and `My.Settings` objects, which provide access to an application's resources and settings.</span></span>  
  
 [<span data-ttu-id="aac9c-117">Vue d’ensemble du modèle d’application Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aac9c-117">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 <span data-ttu-id="aac9c-118">Décrit le modèle [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] de démarrage/arrêt de l’application.</span><span class="sxs-lookup"><span data-stu-id="aac9c-118">Describes the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Application Startup/Shutdown model.</span></span>  
  
 [<span data-ttu-id="aac9c-119">Comment My dépend du type de projet</span><span class="sxs-lookup"><span data-stu-id="aac9c-119">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)  
 <span data-ttu-id="aac9c-120">Donne des détails sur les fonctionnalités `My` qui sont disponibles dans différents types de projets.</span><span class="sxs-lookup"><span data-stu-id="aac9c-120">Gives details on which `My` features are available in different project types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac9c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aac9c-121">See Also</span></span>  
 <span data-ttu-id="aac9c-122"><xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></span><span class="sxs-lookup"><span data-stu-id="aac9c-122"><xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase></span></span>   
 <span data-ttu-id="aac9c-123"><xref:Microsoft.VisualBasic.Devices.Computer></span><span class="sxs-lookup"><span data-stu-id="aac9c-123"><xref:Microsoft.VisualBasic.Devices.Computer></span></span>   
 <span data-ttu-id="aac9c-124"><xref:Microsoft.VisualBasic.ApplicationServices.User></span><span class="sxs-lookup"><span data-stu-id="aac9c-124"><xref:Microsoft.VisualBasic.ApplicationServices.User></span></span>   
 <span data-ttu-id="aac9c-125">[My.Forms (objet)](../../../visual-basic/language-reference/objects/my-forms-object.md) </span><span class="sxs-lookup"><span data-stu-id="aac9c-125">[My.Forms Object](../../../visual-basic/language-reference/objects/my-forms-object.md) </span></span>  
 <span data-ttu-id="aac9c-126">[My.WebServices (objet)](../../../visual-basic/language-reference/objects/my-webservices-object.md) </span><span class="sxs-lookup"><span data-stu-id="aac9c-126">[My.WebServices Object](../../../visual-basic/language-reference/objects/my-webservices-object.md) </span></span>  
 [<span data-ttu-id="aac9c-127">Comment My dépend du type de projet</span><span class="sxs-lookup"><span data-stu-id="aac9c-127">How My Depends on Project Type</span></span>](../../../visual-basic/developing-apps/development-with-my/how-my-depends-on-project-type.md)

