---
title: "Extension des m&#233;tadonn&#233;es &#224; l&#39;aide des attributs | Microsoft Docs"
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
  - "annoter les éléments de programmation"
  - "attributs (.NET Framework), métadonnées"
  - "Common Language Runtime, attributs"
  - "éléments (.NET Framework), attributs"
  - "étendre les métadonnées"
  - "déclarations descriptives de type mot clé"
  - "métadonnées, étendre"
  - "runtime, attributs"
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Extension des m&#233;tadonn&#233;es &#224; l&#39;aide des attributs
Le common language runtime vous permet d'ajouter des déclarations descriptives de type mot clé, appelées attributs, pour annoter les éléments de programmation comme des types, des champs, des méthodes et des propriétés.  Quand vous compilez votre code pour le runtime, il est converti en langage MSIL \(Microsoft Intermediate Language\) et placé dans un fichier exécutable portable avec des métadonnées générées par le compilateur.  Les attributs vous permettent de placer des informations descriptives supplémentaires dans les métadonnées, qui peuvent être extraites à l'aide des services de réflexion du runtime.  Le compilateur crée des attributs quand vous déclarez des instances de classes spéciales qui dérivent de <xref:System.Attribute?displayProperty=fullName>.  
  
 Le .NET Framework utilise des attributs pour différentes raisons et pour résoudre un certain nombre de problèmes.  Les attributs décrivent comment sérialiser les données, spécifient des caractéristiques qui sont utilisées pour appliquer la sécurité et limitent les optimisations du compilateur juste\-à\-temps \(JIT\) pour que le code reste facile à déboguer.  Les attributs peuvent également enregistrer le nom d'un fichier ou l'auteur du code, ou bien contrôler la visibilité des contrôles et des membres pendant le développement des formulaires.  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Application des attributs](../../../docs/standard/attributes/applying-attributes.md)|Décrit comment appliquer un attribut à un élément de votre code.|  
|[Écriture des attributs personnalisés](../../../docs/standard/attributes/writing-custom-attributes.md)|Décrit comment concevoir des classes d'attributs personnalisés.|  
|[Récupération des informations stockées dans les attributs](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|Décrit comment récupérer des attributs personnalisés pour le code qui est chargé dans le contexte d'exécution.|  
|[Métadonnées et composants autodescriptifs](../../../docs/standard/metadata-and-self-describing-components.md)|Fournit une vue d'ensemble des métadonnées et décrit comment elles sont implémentées dans un fichier exécutable portable du .NET Framework.|  
|[Comment : charger des assemblys dans le contexte de réflexion uniquement](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Explique comment récupérer les informations des attributs personnalisés dans le contexte de réflexion uniquement.|  
  
## Référence  
 <xref:System.Attribute?displayProperty=fullName>