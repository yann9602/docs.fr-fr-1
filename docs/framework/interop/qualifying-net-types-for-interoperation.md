---
title: "Qualifying .NET Types for Interoperation | Microsoft Docs"
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
  - "exposing .NET Framework components to COM"
  - "COM interop, qualifying .NET types"
  - "qualifying .NET types for interoperation"
  - "interoperation with unmanaged code, qualifying .NET types"
  - "interoperation with unmanaged code, exposing .NET Framework components"
  - "COM interop, exposing COM components"
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# Qualifying .NET Types for Interoperation
Si vous avez l'intention d'exposer des types figurant dans un assembly à des applications COM, prenez en compte les conditions requises par COM Interop au moment du design.  Les types managés \(classe, interface, structure et énumération\) s'intègrent de façon transparente aux types COM lorsque vous respectez les indications suivantes :  
  
-   Les classes doivent implémenter explicitement des interfaces.  
  
     Même si COM Interop propose un mécanisme permettant de générer automatiquement une interface contenant tous les membres de la classe et les membres de sa classe de base, il est de loin préférable de fournir des interfaces explicites.  L'interface générée de manière automatique est appelée interface de classe.  Pour obtenir des indications, consultez [Présentation de l'interface de classe](http://msdn.microsoft.com/fr-fr/733c0dd2-12e5-46e6-8de1-39d5b25df024).  
  
     Vous pouvez utiliser [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C\# et C\+\+ pour incorporer des définitions d'interface dans votre code, plutôt que de devoir utiliser le langage IDL \(Interface Definition Language\) ou son équivalent.  Pour plus d'informations sur la syntaxe, consultez la documentation sur votre langage.  
  
-   Les types managés doivent être publics.  
  
     Seuls les types publics figurant dans un assembly sont inscrits et exportés vers la bibliothèque de types.  Seuls les types publics sont par conséquent rendus visibles à COM.  
  
     Les types managés exposent des fonctionnalités à un autre code managé pouvant ne pas être exposé à COM.  Par exemple, les constructeurs paramétrés, les méthodes statiques et les champs constants ne sont pas exposés aux clients COM.  De plus, comme le runtime marshale des données à l'intérieur et à l'extérieur d'un type, les données peuvent être copiées ou transformées.  
  
-   Les méthodes, les propriétés, les champs et les événements doivent être publics.  
  
     Les membres des types publics doivent également être publics s'ils doivent être rendus visibles à COM.  Vous pouvez restreindre la visibilité d'un assembly, d'un type public ou des membres publics d'un type public en appliquant <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  Par défaut, tous les membres et les types publics sont visibles.  
  
-   Les types doivent avoir un constructeur public par défaut qui doit être activé à partir de COM.  
  
     Les types publics managés sont rendus visibles à COM.  Sans constructeur par défaut public \(constructeur sans argument\), les clients COM ne peuvent toutefois pas créer le type.  Les clients COM peuvent quand même utiliser le type s'il est activé par d'autres moyens.  
  
-   Les types ne peuvent pas être abstraits.  
  
     Ni les clients COM ni les clients .NET ne peuvent créer des types abstraits.  
  
 Une fois exportée vers COM, la hiérarchie d'héritage d'un type managé est vide.  Le versioning varie également selon les environnements managés et non managés.  Les types exposés à COM ne possèdent pas les mêmes caractéristiques de versioning que les autres types managés.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [Introducing the Class Interface](http://msdn.microsoft.com/fr-fr/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Applying Interop Attributes](../../../docs/framework/interop/applying-interop-attributes.md)   
 [Packaging an Assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)