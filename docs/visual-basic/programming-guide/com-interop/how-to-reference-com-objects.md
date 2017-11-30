---
title: "Comment : référencer les objets COM à partir de Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 694bd74e2b5ae374269accd845fe9178958bf56c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Comment : référencer les objets COM à partir de Visual Basic
Dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], ajouter des références aux objets COM qui possèdent des bibliothèques de types requiert la création d’un assembly d’interopérabilité pour la bibliothèque COM. Les références aux membres de l’objet COM sont routées vers l’assembly PIA et ensuite transmis à l’objet COM réel. Les réponses de l’objet COM sont routées vers l’assembly PIA et transférés vers votre [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] application.  
  
 Vous pouvez référencer un objet COM sans utiliser un assembly d’interopérabilité en incorporant les informations de type pour l’objet COM dans un assembly .NET. Pour incorporer les informations de type, affectez le `Embed Interop Types` propriété `True` pour la référence à l’objet COM. Si vous compilez à l’aide du compilateur de ligne de commande, utilisez la `/link` option pour faire référence à la bibliothèque COM. Pour plus d’informations, consultez [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md).  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]crée automatiquement des assemblys d’interopérabilité lorsque vous ajoutez une référence à une bibliothèque de types à partir de l’environnement de développement intégré (IDE). Lorsque vous travaillez à partir de la ligne de commande, vous pouvez utiliser l’utilitaire Tlbimp pour créer manuellement des assemblys PIA.  
  
### <a name="to-add-references-to-com-objects"></a>Pour ajouter des références aux objets COM  
  
1.  Sur le **projet** menu, choisissez **ajouter une référence** puis cliquez sur le **COM** onglet dans la boîte de dialogue.  
  
2.  Sélectionnez le composant que vous souhaitez utiliser dans la liste des objets COM.  
  
3.  Pour simplifier l’accès à l’assembly d’interopérabilité, ajoutez une `Imports` en haut de la classe ou le module dans lequel vous allez utiliser l’objet COM. Par exemple, l’exemple de code suivant importe l’espace de noms `INKEDLib` pour les objets référencés dans la `Microsoft InkEdit Control 1.0` bibliothèque.  
  
     [!code-vb[VbVbalrInterop#40](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-reference-com-objects_1.vb)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Pour créer un assembly d’interopérabilité à l’aide de Tlbimp  
  
1.  Ajoutez l’emplacement de Tlbimp au chemin de recherche, si elle n’est pas déjà partie du chemin de recherche et vous n’êtes pas actuellement dans le répertoire où il se trouve.  
  
2.  Appelez Tlbimp à partir d’une invite de commandes, en fournissant les informations suivantes :  
  
    -   Nom et l’emplacement de la DLL qui contient la bibliothèque de types  
  
    -   Nom et l’emplacement de l’espace de noms dans lequel les informations doivent être placées  
  
    -   Nom et l’emplacement de l’assembly d’interopérabilité cible  
  
     Le code suivant est fourni à titre d'exemple :  
  
    ```  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Vous pouvez utiliser Tlbimp pour créer des assemblys PIA pour les bibliothèques de types, même pour les objets COM non inscrits. Toutefois, les objets COM référencés par les assemblys PIA doivent être correctement inscrit sur l’ordinateur sur lequel ils doivent être utilisées. Vous pouvez enregistrer un objet COM à l’aide de l’utilitaire Regsvr32 fourni avec le système d’exploitation Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 [Tlbimp.exe (importateur de bibliothèques de types)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [Tlbexp.exe (exportateur de bibliothèques de types)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Procédure pas à pas : implémentation de l’héritage avec les objets COM](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [Dépannage des problèmes liés à l’interopérabilité](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [Imports (instruction) (espace de noms et type .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
