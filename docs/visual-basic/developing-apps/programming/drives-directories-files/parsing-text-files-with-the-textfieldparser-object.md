---
title: "Analyse des fichiers texte avec l’objet TextFieldParser (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files, parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
caps.latest.revision: 20
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ad7407ca1928f9b4a2405bc5831777fbf965b61f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Analyse des fichiers texte avec l’objet TextFieldParser (Visual Basic)
L’objet `TextFieldParser` permet d’analyser et de traiter de très gros fichiers structurés sous forme de colonnes de texte à largeur délimitée, tels que les fichiers journaux ou les informations de base de données héritée. Analyser un fichier texte avec `TextFieldParser` revient à itérer un fichier texte, alors que la méthode d’analyse pour extraire des champs de texte est similaire aux méthodes de manipulation de chaînes utilisées pour segmenter des chaînes délimitées.  
  
## <a name="parsing-different-types-of-text-files"></a>Analyse de fichiers texte de types différents  
 Les fichiers texte peuvent avoir des champs de largeur différente, délimités par un caractère tel qu’une virgule ou un espace de tabulation. Définissez `TextFieldType` et le délimiteur, comme dans l’exemple suivant, qui utilise la méthode `SetDelimiters` pour définir un fichier texte délimité par des tabulations :  
  
 [!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]  
  
 D’autres fichiers texte peuvent avoir des champs de largeur fixe. Dans ce cas, vous devez définir `TextFieldType` sur `FixedWidth` et définir la largeur de chaque champ, comme dans l’exemple suivant. Cet exemple utilise la méthode `SetFieldWidths` pour définir les colonnes de texte : la première colonne a une largeur de 5 caractères, la deuxième de 10 et la troisième de 11 ; la quatrième colonne a une largeur variable.  
  
 [!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]  
  
 Une fois que vous avez défini le format, vous pouvez parcourir le fichier, à l’aide de la méthode `ReadFields`, pour traiter les lignes une par une.  
  
 Si un champ ne correspond pas au format spécifié, une exception <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> est levée. Dans ce cas, les propriétés `ErrorLine` et `ErrorLineNumber` contiennent le texte à l’origine de l’exception et le numéro de ligne de ce texte.  
  
## <a name="parsing-files-with-multiple-formats"></a>Analyse de fichiers avec plusieurs formats  
 La méthode `PeekChars` de l’objet `TextFieldParser` peut être utilisée pour vérifier chaque champ avant de le lire, ce qui vous permet de définir plusieurs formats de champs ainsi que le comportement approprié. Pour plus d’informations, consultez [Guide pratique pour lire des fichiers texte avec plusieurs formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>

