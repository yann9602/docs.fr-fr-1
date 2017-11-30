---
title: "Comment : empêcher une tâche enfant de s’attacher à son parent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4717e3a077648d9db51fe39228209617b384bd0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="05e4d-102">Comment : empêcher une tâche enfant de s’attacher à son parent</span><span class="sxs-lookup"><span data-stu-id="05e4d-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>
<span data-ttu-id="05e4d-103">Ce document montre comment empêcher une tâche enfant de s’attacher à la tâche parente.</span><span class="sxs-lookup"><span data-stu-id="05e4d-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="05e4d-104">Empêcher une tâche enfant de s’attacher à son parent est utile lorsque vous appelez un composant qui est écrit par un tiers, et qui utilise également des tâches.</span><span class="sxs-lookup"><span data-stu-id="05e4d-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="05e4d-105">Par exemple, un composant tiers qui utilise le <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option pour créer un <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> objet peut provoquer des problèmes dans votre code si elle est longue ou lève une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="05e4d-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05e4d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="05e4d-106">Example</span></span>  
 <span data-ttu-id="05e4d-107">L’exemple suivant compare les effets de l’aide des options par défaut pour les effets d’empêcher une tâche enfant de s’attacher au parent.</span><span class="sxs-lookup"><span data-stu-id="05e4d-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="05e4d-108">L’exemple crée un <xref:System.Threading.Tasks.Task> objet qui appelle une bibliothèque tierce qui utilise également un <xref:System.Threading.Tasks.Task> objet.</span><span class="sxs-lookup"><span data-stu-id="05e4d-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="05e4d-109">La bibliothèque tierce utilise le <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option permettant de créer le <xref:System.Threading.Tasks.Task> objet.</span><span class="sxs-lookup"><span data-stu-id="05e4d-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="05e4d-110">L’application utilise le <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option permettant de créer la tâche parente.</span><span class="sxs-lookup"><span data-stu-id="05e4d-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="05e4d-111">Cette option indique à l’exécution pour supprimer la <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> spécification dans les tâches enfants.</span><span class="sxs-lookup"><span data-stu-id="05e4d-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="05e4d-112">Une tâche parente ne se termine pas tant que toutes les tâches enfants terminées, une tâche enfant à exécution longue peut entraîner l’application globale des performances médiocres.</span><span class="sxs-lookup"><span data-stu-id="05e4d-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="05e4d-113">Dans cet exemple, lorsque l’application utilise les options par défaut pour créer une tâche parent, la tâche enfant doit se terminer avant la fin de la tâche parente.</span><span class="sxs-lookup"><span data-stu-id="05e4d-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="05e4d-114">Lorsque l’application utilise la <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, l’enfant n’est pas attachée au parent.</span><span class="sxs-lookup"><span data-stu-id="05e4d-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="05e4d-115">Par conséquent, l’application peut effectuer une tâche supplémentaire une fois la tâche parente et avant qu’il doit attendre la tâche enfant se termine.</span><span class="sxs-lookup"><span data-stu-id="05e4d-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="05e4d-116">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="05e4d-116">Compiling the Code</span></span>  
 <span data-ttu-id="05e4d-117">Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `DenyChildAttach.cs` (`DenyChildAttach.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="05e4d-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DenyChildAttach.cs` (`DenyChildAttach.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="05e4d-118">**csc.exe DenyChildAttach.cs**</span><span class="sxs-lookup"><span data-stu-id="05e4d-118">**csc.exe DenyChildAttach.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="05e4d-119">**vbc.exe DenyChildAttach.vb**</span><span class="sxs-lookup"><span data-stu-id="05e4d-119">**vbc.exe DenyChildAttach.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="05e4d-120">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="05e4d-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e4d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05e4d-121">See Also</span></span>  
 [<span data-ttu-id="05e4d-122">Programmation asynchrone basée sur les tâches</span><span class="sxs-lookup"><span data-stu-id="05e4d-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
