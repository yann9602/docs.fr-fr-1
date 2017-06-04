---
title: "Packaging an Assembly for COM | Microsoft Docs"
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
  - "COM interop, packaging assemblies"
  - "packaging assemblies for COM"
  - "Tlbexp.exe"
  - "TypeLibConverter class"
  - ".NET Services Installation tool"
  - "Assembly Registration tool"
  - "Type Library Exporter"
  - "Reqsvcs.exe"
  - "interoperation with unmanaged code, exposing .NET Framework components"
  - "interoperation with unmanaged code, packaging assemblies"
  - "COM interop, exposing COM components"
  - "Reqasm.exe"
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Packaging an Assembly for COM
Les développeurs COM peuvent bénéficier des informations suivantes sur les types managés qu'ils prévoient d'incorporer dans leur application :  
  
-   une liste des types pouvant être consommés par des applications COM ;  
  
     Certains types managés sont rendus invisibles à COM, d'autres sont visibles mais ne peuvent pas être créés et d'autres enfin sont visibles et peuvent être créés.  Un assembly peut comprendre une combinaison quelconque de types invisibles, visibles, ne pouvant pas être créés et pouvant être créés.  À des fins de précision, identifiez les types figurant dans un assembly que vous avez l'intention d'exposer à COM, spécialement lorsque ces types constituent un sous\-ensemble de types exposés au .NET Framework.  
  
     Pour plus d'informations, consultez [Qualification des types .NET en vue d'une interopérabilité](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
-   des instructions de versioning ;  
  
     Les classes managées qui implémentent l'interface de classe \(une interface générée par COM Interop\) sont soumises à des restrictions de versioning.  
  
     Pour obtenir des indications sur l'utilisation de l'interface de classe, consultez [Présentation de l'interface de classe](http://msdn.microsoft.com/fr-fr/733c0dd2-12e5-46e6-8de1-39d5b25df024).  
  
-   des instructions de déploiement ;  
  
     Les assemblys avec nom fort signés par un éditeur peuvent être installés dans le Global Assembly Cache.  Les assemblys non signés doivent être installés sur l'ordinateur de l'utilisateur en tant qu'assemblys privés.  
  
     Pour plus d'informations, consultez [Aspects de la sécurité des assemblys](../../../docs/framework/app-domains/assembly-security-considerations.md).  
  
-   l'inclusion d'une bibliothèque de types.  
  
     La plupart des types nécessitent une bibliothèque de types lorsqu'ils sont consommés par une application COM.  Vous pouvez générer une bibliothèque de types ou confier cette tâche aux développeurs COM.  Le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] propose les options suivantes pour générer une bibliothèque de types :  
  
    -   [Outil Type Library Exporter](#cpconpackagingassemblyforcomanchor1)  
  
    -   [TypeLibConverter, classe](#cpconpackagingassemblyforcomanchor2)  
  
    -   [Outil Assembly Registration Tool](#cpconpackagingassemblyforcomanchor3)  
  
    -   [Outil .NET Services Installation Tool](#cpconpackagingassemblyforcomanchor4)  
  
     Quel que soit le mécanisme que vous choisissez, seuls les types publics définis dans l'assembly que vous fournissez sont inclus dans la bibliothèque de types générée.  
  
     Vous pouvez empaqueter une bibliothèque de types sous la forme d'un fichier séparé ou l'incorporer en tant que fichier de ressources Win32 dans une application .NET.  Microsoft Visual Basic 6.0 a effectué cette tâche pour vous automatiquement ; toutefois, lorsque vous utilisez [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], vous devez incorporer votre bibliothèque de types manuellement.  Pour obtenir des instructions, consultez [Comment : incorporer des bibliothèques de types comme des ressources Win32 dans les applications .NET](http://msdn.microsoft.com/fr-fr/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44).  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## Outil Type Library Exporter  
 L'outil de ligne de commande [Type Library Exporter \(Tlbexp.exe\)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) permet de convertir les classes et les interfaces figurant dans un assembly en bibliothèque de types COM.  Une fois les informations sur les types de la classe disponibles, les clients COM peuvent créer une instance de la classe .NET et appeler les méthodes de l'instance, comme s'il s'agissait d'un objet COM.  Tlbexp.exe convertit l'intégralité d'un assembly en une seule opération.  Vous ne pouvez pas utiliser Tlbexp.exe pour générer des informations sur les types pour un sous\-ensemble de types définis dans un assembly.  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## TypeLibConverter, classe  
 La classe <xref:System.Runtime.InteropServices.TypeLibConverter> située dans l'espace de noms **System.Runtime.Interop**, convertit les classes et les interfaces figurant dans un assembly en une bibliothèque de types COM.  Cette interface API produit les mêmes informations sur les types que l'outil Type Library Exporter décrit dans la section précédente.  
  
 La classe **TypeLibConverter** implémente l'[interface ITypeLibConverter](frlrfSystemRuntimeInteropServicesITypeLibConverterClassTopic).  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## Outil Assembly Registration Tool  
 L'outil [Assembly Registration Tool \(Regasm.exe\)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) peut générer et inscrire une bibliothèque de types lorsque vous appliquez l'option **\/tlb:**.  Les clients COM exigent que les bibliothèques de types soient installées dans la base de registres Windows.  Sans cette option, Regasm.exe n'inscrit que les types dans un assembly et non la bibliothèque de types.  L'inscription des types dans un assembly et l'inscription de la bibliothèque de types sont deux activités distinctes.  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## Outil .NET Services Installation Tool  
 L'outil [.NET Services Installation Tool \(Regsvcs.exe\)](../../../docs/framework/tools/regsvcs-exe-net-services-installation-tool.md) ajoute des classes managées aux Services de composants Windows 2000 et combine plusieurs tâches dans un seul outil.  Outre le chargement et l'inscription d'un assembly, Regsvcs.exe peut générer, inscrire et installer la bibliothèque de types dans une application COM\+ 1.0 existante.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.TypeLibConverter>   
 <xref:System.Runtime.InteropServices.ITypeLibConverter>   
 [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [Qualifying .NET Types for Interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md)   
 [Introducing the Class Interface](http://msdn.microsoft.com/fr-fr/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Aspects de la sécurité des assemblys](../../../docs/framework/app-domains/assembly-security-considerations.md)   
 [Tlbexp.exe \(Type Library Exporter\)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)   
 [Registering Assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md)   
 [How to: Embed Type Libraries as Win32 Resources in Applications](http://msdn.microsoft.com/fr-fr/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44)