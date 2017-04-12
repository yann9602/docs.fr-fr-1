---
title: "Comment : activer XML IntelliSense dans Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: af67d0ee-a4a6-4abf-9c07-5a8cfe80d111
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 84af19189fa3fc510c8d4f8e408cbb2a393d8b8f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-enable-xml-intellisense-in-visual-basic"></a>Comment : activer XML IntelliSense dans Visual Basic
XML IntelliSense dans Visual Basic fournit le mot intégral des éléments définis dans un schéma XML. Pour activer XML IntelliSense dans Visual Basic, vous devez procédez comme suit :  
  
1.  Obtenir le schéma XSD XML ou les fichiers pour les fichiers XML qui lit ou écrire dans votre application.  
  
2.  Inclure les fichiers de schéma XML dans votre projet.  
  
3.  Importez l’espace de noms cible ou les espaces de noms dans votre projet ou le fichier de code. Espace de noms cible est identifié par le `targetNamespace` ou `tns` attribut de votre schéma XSD.  
  
     Pour importer un espace de noms cible, utilisez la `Imports` instruction, ou ajouter un espace de noms pour tous les fichiers de code dans un projet à l’aide de la **références** page du Concepteur de projets.  
  
 Pour plus d’informations sur les fonctionnalités de XML IntelliSense dans Visual Basic, consultez [XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md). Pour plus d’informations sur l’importation d’espaces de noms XML, consultez [l’instruction Imports (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) ou [Page références, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
 ![lien vers la vidéo](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") pour obtenir une version vidéo de cette rubrique, consultez la page [vidéo Comment : activer XML IntelliSense dans Visual Basic](http://go.microsoft.com/fwlink/?LinkId=102466). Pour une démonstration vidéo connexe, consultez [comment activer XML IntelliSense and Use XML Namespaces ?](http://go.microsoft.com/fwlink/?LinkId=143035).  
  
## <a name="enable-xml-intellisense-in-visual-basic"></a>Activer XML IntelliSense dans Visual Basic  
 Si vous avez un fichier XML, mais vous n’avez pas un fichier de schéma XSD pour lui, dans SP1, vous pouvez créer un fichier de schéma XSD à l’aide de l’Assistant schéma XML vers. Vous pouvez également utiliser l’inférence de schéma dans l’éditeur XML de Visual Studio.  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-the-xml-to-schema-wizard-requires-sp1"></a>Pour créer un fichier de schéma XSD pour un fichier XML à l’aide de l’Assistant schéma XML vers (SP1 requis)  
  
1.  Dans votre projet, cliquez sur **ajouter un nouvel élément** sur la **projet** menu.  
  
2.  Sélectionnez le **Xml au schéma** modèle d’élément à partir la **données** ou **éléments communs** catégories de modèles.  
  
3.  Fournissez un nom de fichier pour le fichier XSD ou les fichiers qui seront stockées dans le jeu de schémas déduits et puis cliquez sur **ajouter**.  
  
4.  Dans le **déduire un schéma XML défini à partir de documents XML** fenêtre, ajoutez un ou plusieurs documents XML pour déduire le jeu de schémas XML.  
  
    -   Pour ajouter des fichiers texte contenant des documents XML à l’aide de l’Explorateur de fichiers, cliquez sur **à partir du fichier**.  
  
    -   Pour ajouter un document XML à partir d’une adresse HTTP, cliquez sur **à partir du Web**.  
  
    -   Pour copier ou taper le contenu d’un document XML dans l’Assistant, cliquez sur **entrer ou coller du XML**.  
  
5.  Lorsque vous avez spécifié toutes les sources de document XML à partir de laquelle vous souhaitez déduire le jeu de schémas XML, cliquez sur **OK** déduire le schéma XML défini. Le jeu de schémas est enregistré dans votre dossier de projet dans un ou plusieurs fichiers XSD. (Pour chaque espace de noms XML dans le schéma, un fichier est créé.)  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-schema-inference-in-the-visual-studio-xml-editor"></a>Pour créer un fichier de schéma XSD pour un fichier XML à l’aide de l’inférence de schéma dans l’éditeur XML de Visual Studio  
  
1.  Modifiez le fichier XML dans le Concepteur XML de Visual Studio.  
  
2.  Lorsque le curseur se trouve dans le fichier XML, le **XML** menu s’affiche. Cliquez sur **Create Schema** sur la **XML** menu. Un fichier XSD est créé à partir du schéma XSD déduit à partir du fichier XML.  
  
3.  Enregistrez le fichier de schéma XSD.  
  
    > [!NOTE]
    >  Différents schémas XSD peuvent être déduits à partir de plusieurs documents XML conçus pour avoir le même schéma. Cela peut se produire lorsque des éléments et attributs particuliers sont trouvées dans un fichier XML et pas dans un autre, ou lorsque les éléments sont inclus dans un ordre différent, par exemple. Vous devez examiner les schémas XSD déduits d’exhaustivité et la précision lorsque vous utilisez l’inférence de schéma XSD.  
  
#### <a name="to-include-an-xsd-schema-file"></a>Pour inclure un fichier de schéma XSD  
  
-   Par défaut, vous ne voyez pas de fichiers XSD dans les projets Visual Basic. Si votre fichier XSD est déjà inclus dans les dossiers de votre projet, cliquez sur le **afficher tous les fichiers** bouton **l’Explorateur de solutions**. Localisez le fichier XSD dans **l’Explorateur de solutions**, cliquez sur le fichier, puis cliquez sur **inclure le fichier dans le projet**.  
  
-   Si votre fichier XSD n’est pas déjà partie de votre projet, dans **l’Explorateur de solutions**, cliquez sur le dossier dans lequel vous souhaitez stocker le fichier XSD, pointez sur **ajouter**, puis cliquez sur **élément existant**. Recherchez votre fichier XSD, puis cliquez **ajouter**.  
  
#### <a name="to-import-an-xml-namespace-in-a-code-file"></a>Pour importer un espace de noms XML dans un fichier de code  
  
1.  Identifiez l’espace de noms cible de schéma XSD.  
  
2.  Au début du fichier de code, ajoutez une `Imports` instruction pour l’espace de noms XML cible, comme illustré dans l’exemple suivant.  
  
     [!code-vb[VbXMLSamples n °&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]  
  
     Pour importer un espace de noms XML en tant que l’espace de noms par défaut, autrement dit, l’espace de noms est appliqué aux éléments XML et les attributs qui n’ont pas un préfixe d’espace de noms, ajoutez un `Imports` instruction pour l’espace de noms XML par défaut. Ne spécifiez pas un préfixe d’espace de noms. Voici un exemple d’un `Imports` instruction.  
  
     [!code-vb[VbXmlSamples&#50;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]  
  
#### <a name="to-import-an-xml-namespace-for-all-files-in-a-project"></a>Pour importer un espace de noms XML pour tous les fichiers dans un projet  
  
1.  Un espace de noms XML importé dans un fichier de code s’applique à ce fichier de code uniquement. Pour importer un espace de noms XML qui s’applique à tous les fichiers de code dans un projet, ouvrez le Concepteur de projets en double-cliquant sur **mon projet** dans **l’Explorateur de solutions**.  
  
2.  Sur le **références** sous l’onglet du **espaces de noms importés** , tapez l’espace de noms cible XML sous la forme d’une déclaration d’espace de noms XML complète (par exemple, `<xmlns: ns="http://sampleNamespace">`). Si l’espace de noms XML cible ne spécifie pas un préfixe d’espace de noms, l’espace de noms sera l’espace de noms XML par défaut pour le projet.  
  
3.  Cliquez sur **ajouter une importation utilisateur**.  
  
## <a name="see-also"></a>Voir aussi  
 [Imports, instruction (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Page Références, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)   
 [XML IntelliSense dans Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)

