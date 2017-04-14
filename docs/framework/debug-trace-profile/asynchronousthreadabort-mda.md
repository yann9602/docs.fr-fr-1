---
title: "asynchronousThreadAbort MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "asynchronous thread aborts"
  - "AsynchronousThreadAbort MDA"
  - "managed debugging assistants (MDAs), asynchronous thread aborts"
  - "threading [.NET Framework], managed debugging assistants"
  - "MDAs (managed debugging assistants), asynchronous thread aborts"
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# asynchronousThreadAbort MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `asynchronousThreadAbort` est activé lorsqu'un thread tente d'introduire un abandon asynchrone dans un autre thread.  Les abandons de thread synchrones n'activent pas le MDA `asynchronousThreadAbort`.  
  
## Symptômes  
 Une panne survient sur une application avec une <xref:System.Threading.ThreadAbortException> non gérée lorsque le thread d'application principal est abandonné.  Si l'exécution de l'application se poursuit, les conséquences peuvent être pires que la panne de l'application et même entraîner l'altération d'autres données.  
  
 Les opérations censées être atomiques ont probablement été interrompues après l'achèvement partiel, laissant les données d'application dans un état imprévisible.  Une <xref:System.Threading.ThreadAbortException> peut être générée à partir de points apparemment aléatoires dans l'exécution de code, souvent à des endroits à partir desquels une exception n'est pas censée survenir.  Il est possible que le code ne puisse pas gérer une telle exception, ce qui provoque un état endommagé.  
  
 Les symptômes peuvent varier considérablement en raison du caractère aléatoire du problème.  
  
## Cause  
 Le code d'un thread a appelé la méthode <xref:System.Threading.Thread.Abort%2A?displayProperty=fullName> sur un thread cible pour introduire un abandon de thread asynchrone.  L'abandon de thread est asynchrone car le code qui effectue l'appel à <xref:System.Threading.Thread.Abort%2A> s'exécute sur un thread différent de la cible de l'opération d'abandon.  Les abandons de thread synchrones ne devraient pas entraîner de problème car le thread qui exécute <xref:System.Threading.Thread.Abort%2A> a dû le faire uniquement à un point de contrôle sécurisé où l'état de l'application est cohérent.  
  
 Les abandons de thread asynchrones présentent un problème car ils sont traités à des stades imprévisibles dans l'exécution du thread cible.  Pour éviter ce problème, le code écrit pour être exécuté sur un thread pouvant être abandonné de cette manière doit gérer une <xref:System.Threading.ThreadAbortException> quasiment à chaque ligne de code, en prenant soin de redonner aux données d'application un état cohérent.  Il n'est pas réaliste d'attendre que le code soit écrit alors que vous connaissez ce problème ou d'écrire du code assurant une protection contre toutes les circonstances possibles.  
  
 Les appels dans du code non managé et les blocs `finally` ne seront pas abandonnés de façon asynchrone mais dès la sortie de l'une de ces catégories.  
  
 La cause peut être difficile à déterminer en raison du caractère aléatoire du problème.  
  
## Résolution  
 Évitez les designs de code qui requièrent l'utilisation d'abandons de thread asynchrones.  Il existe plusieurs approches plus appropriées pour l'interruption d'un thread cible qui ne requièrent pas d'appel à <xref:System.Threading.Thread.Abort%2A>.  L'approche la plus sûre est d'introduire un mécanisme, tel qu'une propriété commune, qui indique au thread cible de demander une interruption.  Le thread cible vérifie ce signal à certains points de contrôle sécurisés.  S'il remarque qu'une interruption a été demandée, il peut s'arrêter correctement.  
  
## Effet sur le runtime  
 Ce MDA n'a aucun effet sur le CLR.  Il signale uniquement des données relatives aux abandons de thread asynchrones.  
  
## Sortie  
 Le MDA signale l'ID du thread qui exécute l'abandon et l'ID du thread qui est la cible de l'abandon.  Ils ne seront jamais identiques car cette opération est limitée aux abandons asynchrones.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <asynchronousThreadAbort />  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 L'activation du MDA `asynchronousThreadAbort` requiert uniquement un appel à <xref:System.Threading.Thread.Abort%2A> sur un thread en cours d'exécution séparé.  Envisagez les conséquences si le contenu de la fonction de démarrage du thread est un jeu d'opérations plus complexes pouvant être interrompu à un stade arbitraire par l'abandon.  
  
```  
using System.Threading;  
void FireMda()  
{  
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });  
    t.Start();  
    // The following line activates the MDA.  
    t.Abort();   
    t.Join();  
}  
```  
  
## Voir aussi  
 <xref:System.Threading.Thread>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)