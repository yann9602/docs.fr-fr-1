---
title: "Type Equivalence and Embedded Interop Types | Microsoft Docs"
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
  - "type equivalence"
  - "embedded interop types"
  - "primary interop assemblies,not necessary in CLR version 4"
  - "NoPIA"
ms.assetid: 78892eba-2a58-4165-b4b1-0250ee2f41dc
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# Type Equivalence and Embedded Interop Types
À compter du [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], le Common Language Runtime prend en charge l'incorporation des informations de type pour les types COM directement dans les assemblys managés, au lieu d'exiger que les assemblys managés obtiennent les informations de type des types COM à partir d'assemblys d'interopérabilité.  Étant donné que les informations de type incorporées incluent uniquement les types et membres réellement utilisés par un assembly managé, deux assemblys managés peuvent avoir des vues très différentes du même type COM.  Chaque assembly managé a un objet <xref:System.Type> différent pour représenter sa vue du type COM.  Le Common Language Runtime prend en charge l'équivalence de type entre ces vues différentes pour les interfaces, structures, énumérations et délégués.  
  
 L'équivalence de type signifie qu'un objet COM passé d'un assembly managé à un autre peut être casté au type managé approprié dans l'assembly de réception.  
  
> [!NOTE]
>  L'équivalence de type et les types interop incorporés simplifient le déploiement des applications et compléments qui utilisent des composants COM, car il n'est pas nécessaire de déployer des assemblys d'interopérabilité avec les applications.  Les développeurs de composants COM partagés doivent toujours créer des assemblys PIA \(Primary Interop Assembly\) s'ils souhaitent que leurs composants soient utilisés par les versions antérieures du .NET Framework.  
  
## Équivalence de type  
 L'équivalence des types COM est prise en charge pour les interfaces, structures, énumérations et délégués.  Les types COM sont équivalents si tout des éléments suivants sont vrais :  
  
-   Les types sont deux interfaces, deux structures, deux énumérations ou deux délégués.  
  
-   Les types ont la même identité, comme décrit dans la section suivante.  
  
-   Les deux types prennent en charge l'équivalence de type, comme décrit dans la section [Marquage de types COM pour l'équivalence de type](#type_equiv).  
  
### Identité de type  
 Deux types sont considérés comme ayant la même identité lorsque leurs portées et identités correspondent, en d'autres termes, s'ils ont chacun l'attribut <xref:System.Runtime.InteropServices.TypeIdentifierAttribute>, et que les deux attributs ont les propriétés <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> et <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A> correspondantes.  La comparaison de <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A> ne respecte pas la casse.  
  
 Si un type ne possède pas l'attribut <xref:System.Runtime.InteropServices.TypeIdentifierAttribute>, ou s'il possède un attribut <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> qui ne spécifie pas de portée et d'identificateur, le type peut quand même être pris en considération pour l'équivalence comme suit :  
  
-   Pour les interfaces, la valeur de l'attribut <xref:System.Runtime.InteropServices.GuidAttribute> est utilisée au lieu de la propriété <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A?displayProperty=fullName>, et la propriété <xref:System.Type.FullName%2A?displayProperty=fullName> \(à savoir le nom de type, notamment l'espace de noms\) est utilisée au lieu de la propriété <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A?displayProperty=fullName>.  
  
-   Pour les structures, les énumérations et les délégués, l'attribut <xref:System.Runtime.InteropServices.GuidAttribute> de l'assembly conteneur est utilisé au lieu de la propriété <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Scope%2A>, et la propriété <xref:System.Type.FullName%2A?displayProperty=fullName> est utilisée au lieu de la propriété <xref:System.Runtime.InteropServices.TypeIdentifierAttribute.Identifier%2A>.  
  
<a name="type_equiv"></a>   
### Marquage de types COM pour l'équivalence de type  
 Vous pouvez marquer un type comme étant prêt pour l'équivalence de type de deux façons :  
  
-   Appliquez l'attribut <xref:System.Runtime.InteropServices.TypeIdentifierAttribute> au type.  
  
-   Faites du type un type d'importation COM.  Une interface est un type d'importation COM si elle possède l'attribut <xref:System.Runtime.InteropServices.ComImportAttribute>.  Une interface, une structure, une énumération ou un délégué est un type d'importation COM si l'assembly dans lequel il\/elle est défini\(e\) possède l'attribut <xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>.  
  
## Voir aussi  
 <xref:System.Type.IsEquivalentTo%2A>   
 [Using COM Types in Managed Code](http://msdn.microsoft.com/fr-fr/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)   
 [Importing a Type Library as an Assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)