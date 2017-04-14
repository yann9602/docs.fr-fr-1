---
title: "moduloObjectHashcode MDA | Microsoft Docs"
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
  - "managed debugging assistants (MDAs), hashcode modulus"
  - "Modulo object hash code"
  - "moduloObjectHashcode MDA"
  - "hashcode modulus"
  - "MDAs (managed debugging assistants), hashcode modulus"
  - "GetHashCode method"
  - "modulus of hashcodes"
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# moduloObjectHashcode MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `moduloObjectHashcode` modifie le comportement de la classe <xref:System.Object> pour exécuter une opération modulo sur le code de hachage retourné par la méthode <xref:System.Object.GetHashCode%2A>.  Le modulo par défaut pour cet Assistant Débogage managé est 1. Dans ce cas, la méthode <xref:System.Object.GetHashCode%2A> retourne 0 pour tous les objets.  
  
## Symptômes  
 Après être passé à une nouvelle version du Common Language Runtime \(CLR\), un programme ne s'exécute plus correctement dans les cas suivants :  
  
-   Le programme n'obtient pas l'objet correct d'un <xref:System.Collections.Hashtable>.  
  
-   L'ordre d'énumération de <xref:System.Collections.Hashtable> est modifié de telle sorte que le programme s'arrête.  
  
-   Deux objets auparavant égaux ne le sont plus.  
  
-   Deux objets auparavant inégaux sont désormais égaux.  
  
## Cause  
 Votre programme peut obtenir l'objet incorrect de <xref:System.Collections.Hashtable> car l'implémentation de la méthode <xref:System.Object.Equals%2A> sur la classe pour obtenir la clé dans <xref:System.Collections.Hashtable> vérifie l'égalité des objets en comparant les résultats de l'appel à la méthode <xref:System.Object.GetHashCode%2A>.  Les codes de hachage ne doivent pas être utilisés pour vérifier l'égalité des objets dans la mesure où deux objets peuvent avoir le même code de hachage même si leurs champs respectifs ont des valeurs différentes.  Ces collisions de codes de hachage, bien que rares en pratique, peuvent se produire  et ont l'effet suivant sur une recherche <xref:System.Collections.Hashtable> : deux clés qui ne sont pas égales semblent être égales et <xref:System.Collections.Hashtable> ne retourne pas l'objet correct.  Pour des raisons de performance, l'implémentation de <xref:System.Object.GetHashCode%2A> peut varier d'une version du runtime à une autre. Par conséquent, des collisions inexistantes dans une version peuvent se produire dans les versions suivantes.  Activez cet Assistant Débogage managé pour vérifier si votre code comporte des bogues en cas de collision de codes de hachage.  Lorsque cet Assistant Débogage managé est activé, la méthode <xref:System.Object.GetHashCode%2A> retourne 0, ce qui se traduit par une collision de tous les codes de hachage.  L'activation de cet Assistant ne doit avoir d'autre effet qu'une exécution plus lente de votre programme.  
  
 L'ordre d'énumération de <xref:System.Collections.Hashtable> peut varier d'une version du runtime à une autre si l'algorithme utilisé pour calculer les codes de hachage de la clé change.  Pour vérifier si votre programme présente une dépendance vis\-à\-vis de l'ordre d'énumération des clés ou des valeurs d'une table de hachage, vous pouvez activer cet Assistant Débogage managé.  
  
## Résolution  
 N'utilisez jamais de codes de hachage en remplacement de l'identité d'objet.  Implémentez la substitution de la méthode <xref:System.Object.Equals%2A?displayProperty=fullName> pour empêcher la comparaison des codes de hachage.  
  
 Ne créez pas de dépendances sur l'ordre des énumérations de clés ou valeurs dans les tables de hachage.  
  
## Effet sur le runtime  
 Les applications s'exécutent plus lentement lorsque cet Assistant Débogage managé est activé.  Il prend simplement le code de hachage qui aurait été retourné et retourne à la place son reste lors de sa division par un modulo.  
  
## Sortie  
 Il n'existe pas de sortie pour cet Assistant Débogage managé.  
  
## Configuration  
 L'attribut `modulus` spécifie le modulo utilisé sur le code de hachage.  La valeur par défaut est 1.  
  
```  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)