---
title: BackgroundWorker, composant
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: bef7b0ab-ce57-475a-a2d6-fb8a702a9417
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cbcbc786c19ad1af74114915b0fd0689d466fcbe
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="backgroundworker-component"></a><span data-ttu-id="bc168-102">BackgroundWorker, composant</span><span class="sxs-lookup"><span data-stu-id="bc168-102">BackgroundWorker Component</span></span>
<span data-ttu-id="bc168-103">Le `BackgroundWorker` composant permet à votre formulaire ou contrôle pour exécuter une opération de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="bc168-103">The `BackgroundWorker` component enables your form or control to run an operation asynchronously.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc168-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bc168-104">In This Section</span></span>  
 [<span data-ttu-id="bc168-105">Vue d'ensemble du composant BackgroundWorker</span><span class="sxs-lookup"><span data-stu-id="bc168-105">BackgroundWorker Component Overview</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component-overview.md)  
 <span data-ttu-id="bc168-106">Décrit le `BackgroundWorker` composant, qui vous donne la possibilité d’exécuter les opérations longues de façon asynchrone (« en arrière-plan »), sur un thread différent du thread d’interface utilisateur de votre application.</span><span class="sxs-lookup"><span data-stu-id="bc168-106">Describes the `BackgroundWorker` component, which gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span>  
  
 [<span data-ttu-id="bc168-107">Procédure pas à pas : exécution d’une opération en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="bc168-107">Walkthrough: Running an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 <span data-ttu-id="bc168-108">Montre comment utiliser le `BackgroundWorker` composant dans le concepteur pour exécuter une opération de longue durée sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="bc168-108">Demonstrates how to use the `BackgroundWorker` component in the designer to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="bc168-109">Guide pratique pour exécuter une opération en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="bc168-109">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 <span data-ttu-id="bc168-110">Montre comment utiliser le `BackgroundWorker` composant d’effectuer une opération de longue durée sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="bc168-110">Demonstrates how to use the `BackgroundWorker` component to run a time-consuming operation on a separate thread.</span></span>  
  
 [<span data-ttu-id="bc168-111">Procédure pas à pas : implémentation d'un formulaire qui utilise une opération d'arrière-plan</span><span class="sxs-lookup"><span data-stu-id="bc168-111">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/walkthrough-implementing-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="bc168-112">Crée une application à l’aide du concepteur qui effectue des calculs mathématiques de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="bc168-112">Creates an application using the designer that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="bc168-113">Comment : implémenter un formulaire qui utilise une opération d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="bc168-113">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 <span data-ttu-id="bc168-114">Crée une application qui effectue des calculs mathématiques de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="bc168-114">Creates an application that does mathematical computations asynchronously.</span></span>  
  
 [<span data-ttu-id="bc168-115">Guide pratique pour télécharger un fichier en arrière-plan</span><span class="sxs-lookup"><span data-stu-id="bc168-115">How to: Download a File in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-download-a-file-in-the-background.md)  
 <span data-ttu-id="bc168-116">Montre comment utiliser le `BackgroundWorker` composant à télécharger un fichier sur un thread distinct.</span><span class="sxs-lookup"><span data-stu-id="bc168-116">Demonstrates how to use the `BackgroundWorker` component to download a file on a separate thread.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bc168-117">Référence</span><span class="sxs-lookup"><span data-stu-id="bc168-117">Reference</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="bc168-118">Décrit cette classe et propose des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="bc168-118">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.RunWorkerCompletedEventArgs>  
 <span data-ttu-id="bc168-119">Décrit le type qui conserve les données pour le <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> événement.</span><span class="sxs-lookup"><span data-stu-id="bc168-119">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <span data-ttu-id="bc168-120">Décrit le type qui conserve les données pour le <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> événement.</span><span class="sxs-lookup"><span data-stu-id="bc168-120">Describes the type that holds data for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bc168-121">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="bc168-121">Related Sections</span></span>  
 [<span data-ttu-id="bc168-122">Vue d’ensemble du modèle asynchrone basé sur les événements</span><span class="sxs-lookup"><span data-stu-id="bc168-122">Event-based Asynchronous Pattern Overview</span></span>](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="bc168-123">Décrit comment le modèle asynchrone permet de profiter des avantages des applications multithreads tout en masquant de nombreux problèmes complexes inhérents à la conception multithread.</span><span class="sxs-lookup"><span data-stu-id="bc168-123">Describes how the asynchronous pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>
