---
title: "How to: Prevent a Child Task from Attaching to its Parent | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tasks, preventing attachments"
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# How to: Prevent a Child Task from Attaching to its Parent
Ce fichier montre comment empêcher une tâche enfant de s'attacher à la tâche parent.  Empêcher une tâche enfant de joindre à son parent est utile lorsque vous appelez un composant écrit par un tiers et qui utilise également des tâches.  Par exemple, un troisième composant qui utilise l'option <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=fullName> pour créer un objet <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> peut causer des problèmes dans votre code s'il est long à s'exécuter ou lève une exception non gérée.  
  
## Exemple  
 L'exemple suivant compare les effets de l'utilisation des options par défaut aux effets d'empêchement à une tâche enfant de se lier à une tâche parent.  Cet exemple crée un objet <xref:System.Threading.Tasks.Task> qui appelle dans une bibliothèque tiers qui utilise également un objet <xref:System.Threading.Tasks.Task>.  La bibliothèque tiers utilise l'option <xref:System.Threading.Tasks.TaskCreationOptions> pour créer l'objet <xref:System.Threading.Tasks.Task>.  L'application utilise l'option <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=fullName> pour créer la tâche parent.  Cette option demande au moment de l'exécution de supprimer la spécification <xref:System.Threading.Tasks.TaskCreationOptions> dans les tâches enfants.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Étant donné qu'une tâche parent ne se termine pas avant que toutes les tâches enfants sont terminées, une tâche enfant à exécution longue peut faire que l'application globale ne s'exécute pas très bien.  Dans cet exemple, lorsque l'application utilise les options par défaut pour créer la tâche parent, la tâche enfant doit terminer avant que la tâche parent ait terminée.  Lorsque l'application utilise l'option <xref:System.Threading.Tasks.TaskCreationOptions?displayProperty=fullName>, la tâche enfant n'est pas jointe à la parent.  Par conséquent, l'application peut exécuter un travail supplémentaire après l'exécution de la tâche parent et avant qu'elle ne doivent attendre la fin de la tâche enfant.  
  
## Compilation du code  
 Copiez l'exemple de code et collez\-le dans un projet Visual Studio , ou collez\-le dans un fichier nommé `DenyChildAttach.cs`\(`DenyChildAttach.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\), exécutez ensuite la commande suivante dans une fenêtre d'invite de commandes Visual Studio .  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe DenyChildAttach.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe DenyChildAttach.vb**  
  
## Programmation fiable  
  
## Voir aussi  
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)