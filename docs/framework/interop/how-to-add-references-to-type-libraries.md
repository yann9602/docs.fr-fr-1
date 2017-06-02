---
title: "How to: Add References to Type Libraries | Microsoft Docs"
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
  - "type libraries"
  - "COM interop, importing type library"
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# How to: Add References to Type Libraries
Quand vous ajoutez une référence à une bibliothèque de types, Visual Studio génère un assembly d'interopérabilité contenant des métadonnées. Si un assembly PIA \(Primary Interop Assembly\) est disponible, Visual Studio utilise l'assembly existant avant de générer un nouvel assembly d'interopérabilité.  
  
### Pour ajouter une référence dans une bibliothèque de types Visual Studio  
  
1.  Installez le fichier COM DLL ou EXE sur votre ordinateur, à moins que le fichier Setup.exe de Windows n'exécute l'installation à votre place.  
  
2.  Choisissez **Projet**, **Ajouter une référence**.  
  
3.  Dans le Gestionnaire de références, choisissez **COM**.  
  
4.  Sélectionnez la bibliothèque de types dans la liste, ou naviguez jusqu'au fichier .tlb.  
  
5.  Cliquez sur **OK**.  
  
6.  Dans l'Explorateur de solutions, ouvrez le menu contextuel pour afficher la référence que vous venez d'ajouter, puis choisissez **Propriétés**.  
  
7.  Dans la fenêtre **Propriétés**, assurez\-vous que la propriété **Incorporer les types d'interopérabilité** a la valeur **True**. Visual Studio incorpore alors les informations de type pour les types COM dans vos fichiers exécutables, en éliminant le besoin de déployer des assemblys PIA \(Primary Interop Assembly\) avec votre application.  
  
> [!NOTE]
>  Les options de menu et de boîte de dialogue peuvent varier en fonction de la version de Visual Studio utilisée.  
  
### Pour ajouter une référence à une bibliothèque de types pour la compilation en ligne de commande  
  
1.  Générez un assembly d'interopérabilité comme décrit dans [How to: Generate Interop Assemblies from Type Libraries](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2.  Utilisez l'option du compilateur [\/link \(Link to COM Assembly\)](../Topic/-link%20\(C%23%20Compiler%20Options\).md) ou [\/link](../Topic/-link%20\(Visual%20Basic\).md) avec le nom de l'assembly d'interopérabilité pour incorporer les informations de type pour les types COM dans vos fichiers exécutables.  
  
## Voir aussi  
 [Importing a Type Library as an Assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)   
 [Exposing COM Components to the .NET Framework](../../../docs/framework/interop/exposing-com-components.md)   
 [Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [\/link \(Link to COM Assembly\)](../Topic/-link%20\(C%23%20Compiler%20Options\).md)   
 [\/link](../Topic/-link%20\(Visual%20Basic\).md)