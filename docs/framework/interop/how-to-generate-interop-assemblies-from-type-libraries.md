---
title: "How to: Generate Interop Assemblies from Type Libraries | Microsoft Docs"
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
  - "importing type library"
  - "interop assemblies, generating"
  - "Type Library Importer"
  - "type libraries"
  - "COM interop, importing type library"
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# How to: Generate Interop Assemblies from Type Libraries
L'outil de ligne de commande [Type Library Importer \(Tlbimp.exe\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) permet de convertir les coclasses et les interfaces figurant dans une bibliothèque de types COM en métadonnées.  Cet outil crée automatiquement un assembly d'interopérabilité et un espace de noms pour les informations sur les types.  Une fois les métadonnées d'une classe disponibles, les clients managés peuvent créer des instances du type COM et appeler ses méthodes, comme s'il s'agissait d'une instance .NET.  Tlbimp.exe convertit en une seule opération l'intégralité d'une bibliothèque de types en métadonnées et ne peut pas générer d'informations sur les types pour un sous\-ensemble de types définis dans une bibliothèque de types.  
  
### Pour générer un assembly d'interopérabilité à partir d'une bibliothèque de types  
  
1.  Utilisez la commande suivante :  
  
     **tlbimp** \<*type\-library\-file*\>  
  
     L'ajout du commutateur **\/out:** produit un assembly d'interopérabilité avec un nom modifié, tel que LOANLib.dll.  La modification du nom de l'assembly d'interopérabilité permet de le distinguer de la DLL COM d'origine et d'empêcher les problèmes liés aux noms en double.  
  
## Exemple  
 La commande suivante produit l'assembly Loanlib.dll dans l' espace de noms `Loanlib`.  
  
```  
tlbimp Loanlib.dll  
```  
  
 La commande suivante produit un assembly d'interopérabilité avec un nom modifié \(LOANLib.dll\).  
  
```  
tlbimp LoanLib.dll /out: LOANLib.dll  
```  
  
## Voir aussi  
 [Importing a Type Library as an Assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)   
 [Exposing COM Components to the .NET Framework](../../../docs/framework/interop/exposing-com-components.md)