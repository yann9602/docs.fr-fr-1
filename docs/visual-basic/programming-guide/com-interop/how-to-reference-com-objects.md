---
title: "How to: Reference COM Objects from Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "COM interop, referencing COM objects"
  - "referencing objects, COM objects from Visual Basic"
  - "objects [Visual Basic], referencing"
  - "COM objects, referencing"
  - "interop assemblies"
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Reference COM Objects from Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

En [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], l'ajout de références aux objets COM qui comportent des bibliothèques de types requiert la création d'un assembly d'interopérabilité pour la bibliothèque COM.  Les références aux membres de l'objet COM sont routées vers l'assembly d'interopérabilité, puis transmises à l'objet COM réel.  Les réponses de l'objet COM sont routées vers l'assembly d'interopérabilité, puis transmises à votre application [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].  
  
 Vous pouvez référencer un objet COM sans utiliser d'assembly d'interopérabilité en incorporant les informations de type de l'objet COM dans un assembly .NET.  Pour incorporer les informations de type, affectez à la propriété `Embed Interop Types` la valeur `True` pour la référence à l'objet COM.  Si vous compilez à l'aide du compilateur de ligne de commande, utilisez l'option `/link` pour référencer la bibliothèque COM.  Pour plus d'informations, consultez [\/link](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] crée automatiquement des assemblys d'interopérabilité lorsque vous ajoutez une référence à une bibliothèque de types à partir de l'environnement de développement intégré \(IDE, Integrated Development Environment\).  Lorsque vous travaillez à partir de la ligne de commande, vous pouvez employer l'utilitaire Tlbimp pour créer manuellement des assemblys d'interopérabilité.  
  
### Pour ajouter des références aux objets COM  
  
1.  Dans le menu **Projet**, sélectionnez **Ajouter une référence**, puis cliquez sur l'onglet **COM** dans la boîte de dialogue.  
  
2.  Sélectionnez le composant à utiliser dans la liste des objets COM.  
  
3.  Pour simplifier l'accès à l'assembly d'interopérabilité, ajoutez une instruction `Imports` tout en haut de la classe ou du module où vous utiliserez l'objet COM.  L'exemple de code suivant importe l'espace de noms `INKEDLib` pour les objets référencés dans la bibliothèque `Microsoft InkEdit Control 1.0`.  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### Pour créer un assembly d'interopérabilité à l'aide de Tlbimp  
  
1.  Ajoutez l'emplacement de Tlbimp au chemin de recherche, s'il n'y figure pas déjà et que vous ne vous trouvez pas actuellement dans le répertoire où il est situé.  
  
2.  Appelez Tlbimp à partir d'une invite de commandes, en fournissant les informations suivantes :  
  
    -   Nom et emplacement de la DLL qui contient la bibliothèque de types  
  
    -   Nom et emplacement de l'espace de noms où les informations doivent être placées  
  
    -   Nom et emplacement de l'assembly d'interopérabilité cible  
  
     Le code suivant en est un exemple :  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Vous pouvez utiliser Tlbimp pour créer des assemblys d'interopérabilité pour les bibliothèques de types, voire pour des objets COM non inscrits.  Toutefois, les objets COM désignés par le biais d'assemblys d'interopérabilité doivent être correctement inscrits sur l'ordinateur sur lequel ils doivent être utilisés.  Vous pouvez inscrire un objet COM à l'aide de l'utilitaire Regsvr32 fourni avec le système d'exploitation Windows.  
  
## Voir aussi  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Tlbimp.exe \(Type Library Importer\)](../Topic/Tlbimp.exe%20\(Type%20Library%20Importer\).md)   
 [Tlbexp.exe \(Type Library Exporter\)](../Topic/Tlbexp.exe%20\(Type%20Library%20Exporter\).md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)