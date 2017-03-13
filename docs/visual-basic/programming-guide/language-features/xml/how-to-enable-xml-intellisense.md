---
title: "How to: Enable XML IntelliSense in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML IntelliSense [Visual Basic]"
  - "XML [Visual Basic], IntelliSense"
  - "IntelliSense [Visual Basic], XML"
ms.assetid: af67d0ee-a4a6-4abf-9c07-5a8cfe80d111
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 25
---
# How to: Enable XML IntelliSense in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

XML IntelliSense dans Visual Basic fournit le mot intégral des éléments définis dans un schéma XML.  Pour activer XML IntelliSense dans Visual Basic, effectuez les opérations suivantes :  
  
1.  Obtenez le fichier schéma XML \(XSD\) ou les XML que lit ou écrit votre application.  
  
2.  Incluez les fichiers schémas XML dans votre projet.  
  
3.  Importez le ou les espaces de noms cibles dans votre fichier de code ou votre fichier projet.  Un espace de noms cible s'identifie par l'attribut `targetNamespace` ou `tns` de votre schéma XSD.  
  
     Pour importer un espace de noms cible, utilisez l'instruction `Imports` ou ajoutez un espace de noms pour tous les fichiers de code du projet, en utilisant la page **Références** du Concepteur de projets.  
  
 Pour plus d'informations sur les fonctionnalités de XML IntelliSense dans Visual Basic, consultez [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md).  Pour plus d'informations sur l'importation d'espaces de noms XML, consultez [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) ou [Page Références, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic).  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
 ![lien vers la vidéo](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") Pour obtenir une version vidéo de cette rubrique, consultez [Vidéo Comment : activer XML IntelliSense dans Visual Basic \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=102466).  Pour une démonstration vidéo connexe, consultez [How Do I Enable XML IntelliSense and Use XML Namespaces?](http://msdn.microsoft.com/fr-fr/vbasic/bb887654.aspx).  
  
## Activer XML IntelliSense dans Visual Basic  
 Si vous avez un fichier XML mais n'avez aucun fichier de schéma XSD correspondant, dans le SP1, vous pouvez créer un fichier de schéma XSD à l'aide de l'Assistant Schéma XML vers.  Vous pouvez également utiliser l'inférence de schéma dans l'Éditeur XML de Visual Studio.  
  
#### Pour créer un fichier de schéma XSD pour un fichier XML à l'aide de l'Assistant Schéma XML vers \(SP1 requis\)  
  
1.  Dans votre projet, cliquez sur **Ajouter un nouvel élément** dans le menu **Projet**.  
  
2.  Sélectionnez le modèle d'élément **Schéma XML vers** dans les catégories de modèles **Données** ou **Éléments communs**.  
  
3.  Indiquez le nom du ou des fichiers XSD dans lesquels sera stocké le jeu de schémas déduits, puis cliquez sur **Ajouter**.  
  
4.  Dans la fenêtre **Déduire le jeu de schémas XML des documents XML**, ajoutez un ou plusieurs documents XML à partir desquels déduire le jeu de schémas XML.  
  
    -   Pour ajouter des fichiers texte qui contiennent des documents XML à l'aide de l'Explorateur de fichiers, cliquez sur **Ajouter à partir d’un fichier**.  
  
    -   Pour ajouter un document XML à partir d'une adresse HTTP, cliquez sur **Ajouter à partir du Web**.  
  
    -   Pour copier ou taper le contenu d'un document XML dans l'Assistant, cliquez sur **Entrer ou coller du code XML**.  
  
5.  Après avoir spécifié toutes les sources de document XML à partir desquelles vous souhaitez déduire le jeu de schémas XML, cliquez sur **OK** pour déduire le jeu de schémas XML.  Le jeu de schémas est enregistré dans un ou plusieurs fichiers XSD dans votre dossier de projet.  \(Un fichier est créé pour chaque espace de noms XML dans le schéma.\)  
  
#### Pour créer un fichier de schéma XSD pour un fichier XML à l'aide de l'inférence de schéma dans l'Éditeur XML de Visual Studio.  
  
1.  Modifiez le fichier XML dans le Concepteur XML Visual Studio.  
  
2.  Lorsque le curseur se trouve dans le fichier XML, le menu **XML** s'affiche.  Cliquez sur **Créer un schéma** dans le menu **XML**.  Un fichier XSD est créé à partir du schéma XSD déduit du fichier XML.  
  
3.  Enregistrez le fichier de schéma XSD.  
  
    > [!NOTE]
    >  Différents schémas XSD peuvent être déduits de plusieurs documents XML conçus pour avoir le même schéma.  Cela peut se produire lorsque des éléments et attributs particuliers sont présents dans un fichier XML et pas dans un autre ou lorsque les éléments sont inclus dans un ordre différent, par exemple.  Vous devez passer en revue les schémas XSD déduits par souci d'exhaustivité et d'exactitude lorsque vous utilisez l'inférence de schéma XSD.  
  
#### Pour inclure un fichier de schéma XSD  
  
-   Par défaut, vous ne pouvez pas consulter de fichiers XSD dans les projets Visual Basic.  Si votre fichier XSD est déjà inclus dans les dossiers de votre projet, cliquez sur le bouton **Afficher tous les fichiers** dans l'**Explorateur de solutions**.  Localisez le fichier XSD dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier et cliquez sur **Inclure le fichier dans le projet**.  
  
-   Si votre fichier XSD ne fait pas déjà partie de votre projet, dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le dossier dans lequel vous souhaitez stocker le fichier XSD, pointez sur **Ajouter**, puis cliquez sur **Élément existant**.  Recherchez votre fichier XSD puis cliquez sur **Ajouter**.  
  
#### Pour importer un espace de noms XML dans un fichier de code  
  
1.  Identifiez l'espace de noms cible de schéma XSD.  
  
2.  Au début du fichier de code, ajoutez une instruction `Imports` pour l'espace de noms XML cible, comme indiqué à l'exemple suivant.  
  
     [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]  
  
     Pour importer un espace de noms XML en tant qu'espace de noms par défaut, à savoir un espace de noms appliqué aux éléments et attributs XML sans préfixe d'espace de noms, ajoutez une instruction `Imports` pour l'espace de noms XML cible par défaut.  Ne spécifiez pas de préfixe d'espace de noms.  Ce qui suit est un exemple d'instruction `Imports`.  
  
     [!code-vb[VbXmlSamples#50](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]  
  
#### Pour importer un espace de noms XML pour tous les fichiers d'un projet  
  
1.  Un espace de noms XML importé dans un fichier de code ne s'applique qu'à ce fichier de code.  Pour importer un espace de noms XML qui s'applique à tous les fichiers de code d'un projet, ouvrez le Concepteur de projets en double\-cliquant sur **My Project** dans l'**Explorateur de solutions**.  
  
2.  À la page de l'onglet **Références**, dans la zone **Espaces de noms importés**, tapez l'espace de noms XML cible sous la forme d'une déclaration d'espace de noms XML complète \(par exemple, `<xmlns: ns="http://sampleNamespace">`\).  Si l'espace de noms XML cible ne spécifie aucun préfixe d'espace de noms, l'espace de noms par défaut du projet est adopté.  
  
3.  Cliquez sur **Ajouter une importation utilisateur**.  
  
## Voir aussi  
 [Imports Statement \(XML Namespace\)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Page Références, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/references-page-project-designer-visual-basic)   
 [XML IntelliSense in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)