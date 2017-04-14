---
title: "memberInfoCacheCreation MDA | Microsoft Docs"
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
  - "member info cache creation"
  - "MemberInfoCacheCreation MDA"
  - "reflection, run-time errors"
  - "MDAs (managed debugging assistants), cache"
  - "cache [.NET Framework], reflection"
  - "managed debugging assistants (MDAs), cache"
  - "MemberInfo cache"
ms.assetid: 5abdad23-1335-4744-8acb-934002c0b6fe
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# memberInfoCacheCreation MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `memberInfoCacheCreation` est activé lors de la création d'un cache <xref:System.Reflection.MemberInfo>.  C'est généralement l'indication d'un programme qui utilise des fonctionnalités de réflexion coûteuses en ressources.  
  
## Symptômes  
 Le jeu de travail d'un programme augmente car le programme utilise la réflexion, coûteuse en ressources.  
  
## Cause  
 Les opérations de réflexion qui concernent des objets <xref:System.Reflection.MemberInfo> sont considérées comme coûteuses en ressources car elles doivent lire des métadonnées stockées dans des pages passives et elles indiquent généralement que le programme utilise un scénario à liaison tardive.  
  
## Résolution  
 Vous pouvez déterminer l'endroit du programme qui utilise la réflexion en activant cet Assistant Débogage managé et en exécutant ensuite votre code dans un débogueur ou en attachant un débogueur lorsque l'Assistant Débogage managé est activé.  Sous un débogueur, vous obtiendrez une trace de la pile montrant l'endroit où le cache <xref:System.Reflection.MemberInfo> a été créé et à partir de là, vous pouvez déterminer l'endroit où votre programme utilise la réflexion.  
  
 La résolution dépend des objectifs du code.  Cet Assistant Débogage managé vous avertit que votre programme possède un scénario à liaison tardive.  Vous pouvez souhaiter déterminer si vous pouvez le remplacer par un scénario à liaison anticipée ou prendre en compte les performances du scénario à liaison tardive.  
  
## Effet sur le runtime  
 Cet Assistant Débogage managé est activé pour chaque cache <xref:System.Reflection.MemberInfo> créé.  L'impact sur les performances est négligeable.  
  
## Sortie  
 L'Assistant Débogage managé génère un message en sortie indiquant la création du cache <xref:System.Reflection.MemberInfo>.  Utilisez un débogueur pour obtenir une trace de la pile indiquant l'endroit où votre programme utilise la réflexion.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <memberInfoCacheCreation/>  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 Cet exemple de code activera l'Assistant Débogage managé `memberInfoCacheCreation`.  
  
```  
using System;  
  
public class Exe  
{  
    public static void Main()  
    {  
        typeof(object).GetMethods();  
    }  
}  
```  
  
## Voir aussi  
 <xref:System.Reflection.MemberInfo>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)