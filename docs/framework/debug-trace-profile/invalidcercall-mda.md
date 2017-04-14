---
title: "invalidCERCall MDA | Microsoft Docs"
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
  - "invalid CER calls"
  - "InvalidCERCall MDA"
  - "MDAs (managed debugging assistants), CER calls"
  - "constrained execution regions"
  - "CER calls"
  - "managed debugging assistants (MDAs), CER calls"
ms.assetid: c4577410-602e-44e5-9dab-fea7c55bcdfe
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# invalidCERCall MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `invalidCERCall` est activé en cas d'appel, dans le graphique de la région d'exécution limitée, à une méthode qui ne possède aucun contrat de fiabilité ou un contrat excessivement faible.  Un contrat faible est un contrat qui déclare que la pire altération d'état envisageable dépasse la portée de l'instance passée à l'appel. En d'autres termes, le <xref:System.AppDomain> ou l'état du processus peut être endommagé ou il ne sera pas toujours possible de calculer son résultat de façon déterministe lors de son appel dans une région d'exécution limitée.  
  
## Symptômes  
 Résultats inattendus lors de l'exécution du code dans une région d'exécution limitée.  Les symptômes ne sont pas spécifiques.  Il peut s'agir d'une <xref:System.OutOfMemoryException> inattendue, d'une <xref:System.Threading.ThreadAbortException> ou d'autres exceptions lors d'un appel dans la méthode peu fiable dans la mesure où le runtime ne l'a pas préparée à l'avance ou ne l'a pas protégée contre des exceptions <xref:System.Threading.ThreadAbortException> au moment de l'exécution.  Il existe toutefois une menace bien plus grave : toute exception résultant de la méthode au moment de l'exécution est susceptible de laisser le <xref:System.AppDomain> ou le processus dans un état instable, ce qui est contraire à l'objectif d'une région d'exécution limitée.  En effet, une région d'exécution limitée est créée dans le but d'éviter des altérations d'état de ce type.  Les symptômes d'un état altéré sont spécifiques à l'application étant donné que la définition d'un état cohérent diffère d'une application à l'autre.  
  
## Cause  
 Le code dans une région d'exécution limitée appelle une fonction sans <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> ou avec un <xref:System.Runtime.ConstrainedExecution.ReliabilityContractAttribute> faible qui n'est pas compatible avec une exécution au sein d'une région d'exécution limitée.  
  
 En termes de syntaxe du contrat de la fiabilité, un contrat faible est un contrat qui ne spécifie pas de valeur d'énumération <xref:System.Runtime.ConstrainedExecution.Consistency> ou qui spécifie une valeur <xref:System.Runtime.ConstrainedExecution.Consistency> de <xref:System.Runtime.ConstrainedExecution.Consistency>, <xref:System.Runtime.ConstrainedExecution.Consistency> ou <xref:System.Runtime.ConstrainedExecution.Cer>.  Chacune de ces conditions indique que le code appelé peut empêcher le reste du code de la région d'exécution limitée de conserver un état cohérent.  Les régions d'exécution limitée permettent au code de traiter des erreurs de façon très déterministe, en conservant des invariantes internes importantes pour l'application et en lui permettant de poursuivre son exécution en présence d'erreurs transitoires telles que les exceptions de mémoire insuffisante.  
  
 L'activation de cet Assistant Débogage managé indique une possibilité d'échec de la méthode appelée dans la région d'exécution limitée d'une façon que l'appelant n'avait pas prévue ou qui laisse <xref:System.AppDomain> ou le processus dans un état altéré ou irrécupérable.  Il est évidemment possible que le code appelé s'exécute correctement et qu'il ne s'agisse que d'un simple problème de contrat manquant.  Toutefois, les problèmes associés à l'écriture de code fiable sont délicats et l'absence d'un contrat est souvent le signe que le code peut ne pas s'exécuter correctement.  Un contrat est un indicateur de la fiabilité du codage du programmeur et la promesse que ces garanties ne changeront pas lors des futures révisions du code.  En d'autres termes, les contrats sont des déclarations d'intention et pas uniquement des détails d'implémentation.  
  
 Dans la mesure où toute méthode avec un contrat faible ou inexistant peut potentiellement échouer de diverses façons, souvent imprévisibles, le runtime ne tente de supprimer de la méthode aucun de ses propres échecs imprévisibles, introduits notamment par une compilation JIT en différé, par un remplissage du dictionnaire des génériques ou par des abandons de thread.  En d'autres termes, lorsque cet Assistant Débogage managé est activé, il indique que le runtime n'a pas inclus la méthode appelée dans la région d'exécution limitée en cours de définition ; le graphique des appels a été interrompu au niveau de ce nœud, car toute poursuite de la préparation de ce sous\-arbre peut contribuer à masquer l'erreur potentielle.  
  
## Résolution  
 Ajoutez un contrat de fiabilité valide à la fonction ou évitez d'utiliser cet appel de fonction.  
  
## Effet sur le runtime  
 L'appel à un contrat faible à partir d'une région d'exécution limitée peut empêcher cette région d'exécution limitée d'achever ses opérations.  Cela peut aboutir à l'altération de l'état du processus du <xref:System.AppDomain>.  
  
## Sortie  
 L'exemple suivant illustre une sortie de cet Assistant Débogage managé.  
  
 `Method 'MethodWithCer', while executing within a constrained execution region, makes a call at IL offset 0x000C to 'MethodWithWeakContract', which does not have a sufficiently strong reliability contract and might cause non-deterministic results.`  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidCERCall />  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>   
 <xref:System.Runtime.ConstrainedExecution>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)