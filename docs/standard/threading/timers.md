---
title: "Timers | Microsoft Docs"
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
  - "threading [.NET Framework], timers"
  - "timers, about timers"
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Timers
Les minuteries \(Timers\) sont des objets légers qui vous permettent de spécifier qu'un délégué est appelé à un moment donné.  Un thread du pool effectue l'opération d'attente.  
  
 L'utilisation de la classe <xref:System.Threading.Timer?displayProperty=fullName> est simple.  Vous créez, en passant un délégué <xref:System.Threading.TimerCallback> à la méthode de rappel, un **Timer**, objet représentant l'état qui est passé au rappel, un temps de déclenchement initial et un temps représentant l'intervalle entre les appels du rappel.  Pour annuler une minuterie en attente, appelez la fonction **Timer.Dispose**.  
  
> [!NOTE]
>  Il existe deux autres classes de minuterie \(Timer\).  La classe <xref:System.Windows.Forms.Timer?displayProperty=fullName> est un contrôle qui utilise les concepteurs visuels et est conçu pour être utilisé dans des contextes d'interface utilisateur ; il déclenche des événements sur le thread d'interface utilisateur.  Comme la classe <xref:System.Timers.Timer?displayProperty=fullName> dérive de <xref:System.ComponentModel.Component>, elle peut être utilisée avec les concepteurs visuels ; elle déclenche également des événements, mais sur un thread <xref:System.Threading.ThreadPool>.  La classe <xref:System.Threading.Timer?displayProperty=fullName> effectue des rappels sur un thread <xref:System.Threading.ThreadPool> et n'utilise pas du tout le modèle d'événement.  Elle fournit également un objet d'état à la méthode de rappel, à la différence des autres minuteries \(Timers\).  Elle est extrêmement légère.  
  
 L'exemple de code suivant démarre une minuterie \(Timer\) qui se déclenche après une seconde \(1000 millisecondes\) et marque chaque seconde jusqu'à ce que vous appuyiez sur la touche **ENTRÉE**.  La variable qui contient la référence à la minuterie \(Timer\) est un champ de niveau classe, afin d'empêcher que la minuterie fasse l'objet d'un garbage collection au cours de son exécution.  Pour plus d'informations sur un garbage collection agressif, consultez <xref:System.GC.KeepAlive%2A>.  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## Voir aussi  
 <xref:System.Threading.Timer>   
 [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md)