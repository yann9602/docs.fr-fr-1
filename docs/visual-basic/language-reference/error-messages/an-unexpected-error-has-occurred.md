---
title: "Une erreur inattendue s’est produite, car une ressource de système d’exploitation requise pour le démarrage de l’instance unique ne peut pas être acquis | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
dev_langs:
- VB
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: 10
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 03ab2d1c746fbc28c0c6f3e59371cc6bbd4050cd
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="29d14-102">Une erreur inattendue s'est produite parce qu'une ressource de système d'exploitation requise pour le démarrage de l'instance unique ne peut pas être acquise</span><span class="sxs-lookup"><span data-stu-id="29d14-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="29d14-103">L'application n'a pas pu obtenir une ressource nécessaire du système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="29d14-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="29d14-104">Ce problème peut avoir certaines des causes suivantes :</span><span class="sxs-lookup"><span data-stu-id="29d14-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="29d14-105">L'application n'est pas autorisée à créer des objets de système d'exploitation nommés.</span><span class="sxs-lookup"><span data-stu-id="29d14-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="29d14-106">Le Common Language Runtime n'est pas autorisé à créer des fichiers mappés sur la mémoire.</span><span class="sxs-lookup"><span data-stu-id="29d14-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="29d14-107">L'application doit accéder à un objet de système d'exploitation, mais un autre processus l'utilise.</span><span class="sxs-lookup"><span data-stu-id="29d14-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="29d14-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="29d14-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="29d14-109">Vérifiez que l'application dispose d'autorisations suffisantes pour créer des objets de système d'exploitation nommés.</span><span class="sxs-lookup"><span data-stu-id="29d14-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2.  <span data-ttu-id="29d14-110">Veillez à ce que le Common Language Runtime dispose d'autorisations suffisantes pour créer des fichiers mappés sur la mémoire.</span><span class="sxs-lookup"><span data-stu-id="29d14-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3.  <span data-ttu-id="29d14-111">Redémarrez l'ordinateur pour annuler tout processus susceptible d'utiliser la ressource permettant de se connecter à l'application de l'instance d'origine.</span><span class="sxs-lookup"><span data-stu-id="29d14-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4.  <span data-ttu-id="29d14-112">Notez les circonstances dans lesquelles l'erreur s'est produite, puis contactez les services de support technique Microsoft</span><span class="sxs-lookup"><span data-stu-id="29d14-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29d14-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29d14-113">See Also</span></span>  
 <span data-ttu-id="29d14-114">[Page Application, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="29d14-114">[Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="29d14-115"> [Principes de base du débogueur](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span><span class="sxs-lookup"><span data-stu-id="29d14-115"> [Debugger Basics](https://docs.microsoft.com/visualstudio/debugger/debugger-basics) </span></span>  
<span data-ttu-id="29d14-116"> [Nous contacter](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="29d14-116"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
