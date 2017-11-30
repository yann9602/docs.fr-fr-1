---
title: "Impossible de connecter cette application à instance unique à l’instance d’origine"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fbc8458231c36f3af9ca4de524e01e19a162ee47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="97f71-102">Impossible de connecter cette application à instance unique à l’instance d’origine</span><span class="sxs-lookup"><span data-stu-id="97f71-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="97f71-103">Impossible de connecter cette application à instance unique à l'instance d'origine.</span><span class="sxs-lookup"><span data-stu-id="97f71-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="97f71-104">Ce problème peut avoir les causes suivantes :</span><span class="sxs-lookup"><span data-stu-id="97f71-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="97f71-105">L'instance d'origine a cessé de répondre.</span><span class="sxs-lookup"><span data-stu-id="97f71-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="97f71-106">L'application n'a pas l'autorisation de créer des objets du noyau.</span><span class="sxs-lookup"><span data-stu-id="97f71-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="97f71-107">Pour plus d’informations sur les objets du noyau, consultez [mutex](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="97f71-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="97f71-108">Le nom de base des objets du noyau est une concaténation entre le GUID de l'assembly, le numéro de la version principale et le numéro de la version secondaire.</span><span class="sxs-lookup"><span data-stu-id="97f71-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="97f71-109">Le nom de base pourrait être, par exemple, `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="97f71-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="97f71-110">Pour corriger cette erreur lors du développement d’une application</span><span class="sxs-lookup"><span data-stu-id="97f71-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="97f71-111">Vérifiez que l’application continue de répondre.</span><span class="sxs-lookup"><span data-stu-id="97f71-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="97f71-112">Vérifiez que l’application dispose d’autorisations suffisantes pour créer des objets noyaux.</span><span class="sxs-lookup"><span data-stu-id="97f71-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="97f71-113">Redémarrez l’instance d’origine de l’application.</span><span class="sxs-lookup"><span data-stu-id="97f71-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="97f71-114">Redémarrez l’ordinateur pour annuler tout processus susceptible d’utiliser la ressource permettant de se connecter à l’application de l’instance d’origine.</span><span class="sxs-lookup"><span data-stu-id="97f71-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="97f71-115">Notez les circonstances dans lesquelles l’erreur s’est produite, puis contactez les services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="97f71-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f71-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97f71-116">See Also</span></span>  
 [<span data-ttu-id="97f71-117">NIB : Comment : spécifier le comportement d’instanciation pour une Application (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97f71-117">NIB: How to: Specify Instancing Behavior for an Application (Visual Basic)</span></span>](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e)  
 [<span data-ttu-id="97f71-118">Principes de base du débogueur</span><span class="sxs-lookup"><span data-stu-id="97f71-118">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="97f71-119">PAVEOVER Support technique et accessibilité</span><span class="sxs-lookup"><span data-stu-id="97f71-119">PAVEOVER Product Support and Accessibility</span></span>](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)
