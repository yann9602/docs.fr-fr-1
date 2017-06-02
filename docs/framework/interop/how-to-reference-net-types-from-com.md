---
title: "How to: Reference .NET Types from COM | Microsoft Docs"
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
  - "COM interop, referencing .NET types"
  - "interoperation with unmanaged code, referencing .NET types"
  - "referencing .NET types"
  - "interoperation with unmanaged code, importing type library"
  - "type libraries"
  - "COM interop, importing type library"
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# How to: Reference .NET Types from COM
Du point de vue du code client et serveur, les différences entre COM et le .NET Framework sont largement invisibles.  Les clients Microsoft Visual Basic peuvent afficher un objet .NET dans l'explorateur d'objets, qui expose les méthodes d'objet, la syntaxe, les propriétés et les champs, exactement comme s'il s'agissait de tout autre objet COM.  
  
 Le processus d'importation d'une bibliothèque de types est légèrement plus compliqué pour les clients C\+\+, même si vous utilisez les mêmes outils pour exporter des métadonnées vers une bibliothèque de types COM.  Pour référencer des objets membres .NET à partir d'un client C\+\+ non managé, référencez le fichier TLB \(produit à l'aide de Tlbexp.exe\) avec la directive **\#import**.  Lors du référencement d'une bibliothèque de types à partir de C\+\+, vous devez soit spécifier l'option **raw\_interfaces\_only**, soit importer les définitions dans la bibliothèque de classes de base Mscorlib.tlb.  
  
### Pour importer une bibliothèque  
  
-   Spécifiez l'option **raw\_interfaces\_only** dans la directive **\#import**.  Par exemple :  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     ou  
  
-   Ajoutez une directive \#import pour Mscorlib.tlb.  Par exemple :  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## Voir aussi  
 [Exposing .NET Framework Components to COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)   
 [Registering Assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md)   
 [Calling a .NET Object](http://msdn.microsoft.com/fr-fr/40c9626c-aea6-4bad-b8f0-c1de462efd33)   
 [Deploying an Application for COM Access](http://msdn.microsoft.com/fr-fr/fb63564c-c1b9-4655-a094-a235625882ce)