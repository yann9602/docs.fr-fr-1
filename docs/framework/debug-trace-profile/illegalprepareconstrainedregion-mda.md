---
title: "illegalPrepareConstrainedRegion MDA | Microsoft Docs"
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
  - "PrepareConstrainedRegions method"
  - "managed debugging assistants (MDAs), illegal PrepareConstrainedRegions"
  - "try/catch exception handling, managed debugging assistants"
  - "IllegalPrepareConstrainedRegions MDA"
  - "MDAs (managed debugging assistants), illegal PrepareConstrainedRegions"
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# illegalPrepareConstrainedRegion MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `illegalPrepareConstrainedRegion` est activé lorsqu'un appel de méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=fullName> ne précède pas immédiatement l'instruction `try` du gestionnaire d'exceptions.  Cette restriction étant au niveau MSIL, il est permis d'avoir une source générant du non\-code entre l'appel et `try`, telle que les commentaires.  
  
## Symptômes  
 Une région d'exécution limitée \(CER, Constrained Execution Region\) qui n'est jamais traitée comme telle, mais comme un bloc de gestion des exceptions simple \(`finally` ou `catch`\).  Par conséquent, la région ne s'exécute pas en cas de mémoire insuffisante ou d'abandon de thread.  
  
## Cause  
 Le modèle de préparation pour une CER n'est pas suivi correctement.  Événement d'erreur.  L'appel de la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> utilisé pour marquer des gestionnaires d'exceptions comme introduisant une CER dans leurs blocs `catch`\/`finally`\/`fault`\/`filter` doit être utilisé immédiatement avant l'instruction `try`.  
  
## Résolution  
 Assurez\-vous que l'appel à <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> se produit immédiatement avant l'instruction `try` `` .  
  
## Effet sur le runtime  
 Ce MDA n'a aucun effet sur le CLR.  
  
## Sortie  
 Le MDA affiche le nom de la méthode qui appelle la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>, l'offset MSIL et un message indiquant que l'appel ne précède pas immédiatement le début du bloc try.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 L'exemple de code suivant illustre le modèle qui provoque l'activation de ce MDA.  
  
```  
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)