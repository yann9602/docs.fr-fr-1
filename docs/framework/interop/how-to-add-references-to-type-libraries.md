---
title: "Guide pratique pour ajouter des références aux bibliothèques de types"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a0c4fc9b96ec310e20839be851cfddbb34e09201
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-add-references-to-type-libraries"></a>Guide pratique pour ajouter des références aux bibliothèques de types
Quand vous ajoutez une référence à une bibliothèque de types, Visual Studio génère un assembly d'interopérabilité contenant des métadonnées. Si un assembly PIA (Primary Interop Assembly) est disponible, Visual Studio utilise l'assembly existant avant de générer un nouvel assembly d'interopérabilité.  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>Pour ajouter une référence dans une bibliothèque de types Visual Studio  
  
1.  Installez le fichier COM DLL ou EXE sur votre ordinateur, à moins que le fichier Setup.exe de Windows n'exécute l'installation à votre place.  
  
2.  Choisissez **Projet**, **Ajouter une référence**.  
  
3.  Dans le Gestionnaire de références, choisissez **COM**.  
  
4.  Sélectionnez la bibliothèque de types dans la liste, ou naviguez jusqu'au fichier .tlb.  
  
5.  Cliquez sur **OK**.  
  
6.  Dans l’Explorateur de solutions, ouvrez le menu contextuel pour afficher la référence que vous venez d’ajouter, puis choisissez **Propriétés**.  
  
7.  Dans la fenêtre **Propriétés**, vérifiez que la propriété **Incorporer les types interop** a la valeur **True**. Visual Studio incorpore alors les informations de type pour les types COM dans vos fichiers exécutables, en éliminant le besoin de déployer des assemblys PIA (Primary Interop Assembly) avec votre application.  
  
> [!NOTE]
>  Les options de menu et de boîte de dialogue peuvent varier en fonction de la version de Visual Studio utilisée.  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>Pour ajouter une référence à une bibliothèque de types pour la compilation en ligne de commande  
  
1.  Générez un assembly d’interopérabilité comme décrit dans [Guide pratique pour générer des assemblys d’interopérabilité à partir de bibliothèques de types](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
2.  Utilisez l’option du compilateur [/link (Options du compilateur C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) ou [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) avec le nom de l’assembly d’interopérabilité afin d’incorporer les informations de type pour les types COM dans vos fichiers exécutables.  
  
## <a name="see-also"></a>Voir aussi  
 [Importation d’une bibliothèque de types sous la forme d’un assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)   
 [Exposition de composants COM au .NET Framework](../../../docs/framework/interop/exposing-com-components.md)   
 [Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)   
 [Procédure pas à pas : incorporation de types provenant d’assemblys managés](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)   
 [/link (Options du compilateur C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md)   
 [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md)

