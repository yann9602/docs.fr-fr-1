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
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="f1767-102">Analyse des fichiers texte avec l’objet TextFieldParser (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1767-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>
<span data-ttu-id="f1767-103">L’objet `TextFieldParser` permet d’analyser et de traiter de très gros fichiers structurés sous forme de colonnes de texte à largeur délimitée, tels que les fichiers journaux ou les informations de base de données héritée.</span><span class="sxs-lookup"><span data-stu-id="f1767-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="f1767-104">Analyser un fichier texte avec `TextFieldParser` revient à itérer un fichier texte, alors que la méthode d’analyse pour extraire des champs de texte est similaire aux méthodes de manipulation de chaînes utilisées pour segmenter des chaînes délimitées.</span><span class="sxs-lookup"><span data-stu-id="f1767-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="f1767-105">Analyse de fichiers texte de types différents</span><span class="sxs-lookup"><span data-stu-id="f1767-105">Parsing different types of text files</span></span>  
 <span data-ttu-id="f1767-106">Les fichiers texte peuvent avoir des champs de largeur différente, délimités par un caractère tel qu’une virgule ou un espace de tabulation.</span><span class="sxs-lookup"><span data-stu-id="f1767-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="f1767-107">Définissez `TextFieldType` et le délimiteur, comme dans l’exemple suivant, qui utilise la méthode `SetDelimiters` pour définir un fichier texte délimité par des tabulations :</span><span class="sxs-lookup"><span data-stu-id="f1767-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 <span data-ttu-id="f1767-108">[!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f1767-108">[!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]</span></span>  
  
 <span data-ttu-id="f1767-109">D’autres fichiers texte peuvent avoir des champs de largeur fixe.</span><span class="sxs-lookup"><span data-stu-id="f1767-109">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="f1767-110">Dans ce cas, vous devez définir `TextFieldType` sur `FixedWidth` et définir la largeur de chaque champ, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f1767-110">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="f1767-111">Cet exemple utilise la méthode `SetFieldWidths` pour définir les colonnes de texte : la première colonne a une largeur de 5 caractères, la deuxième de 10 et la troisième de 11 ; la quatrième colonne a une largeur variable.</span><span class="sxs-lookup"><span data-stu-id="f1767-111">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 <span data-ttu-id="f1767-112">[!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f1767-112">[!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]</span></span>  
  
 <span data-ttu-id="f1767-113">Une fois que vous avez défini le format, vous pouvez parcourir le fichier, à l’aide de la méthode `ReadFields`, pour traiter les lignes une par une.</span><span class="sxs-lookup"><span data-stu-id="f1767-113">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="f1767-114">Si un champ ne correspond pas au format spécifié, une exception <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> est levée.</span><span class="sxs-lookup"><span data-stu-id="f1767-114">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="f1767-115">Dans ce cas, les propriétés `ErrorLine` et `ErrorLineNumber` contiennent le texte à l’origine de l’exception et le numéro de ligne de ce texte.</span><span class="sxs-lookup"><span data-stu-id="f1767-115">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="f1767-116">Analyse de fichiers avec plusieurs formats</span><span class="sxs-lookup"><span data-stu-id="f1767-116">Parsing files with multiple formats</span></span>  
 <span data-ttu-id="f1767-117">La méthode `PeekChars` de l’objet `TextFieldParser` peut être utilisée pour vérifier chaque champ avant de le lire, ce qui vous permet de définir plusieurs formats de champs ainsi que le comportement approprié.</span><span class="sxs-lookup"><span data-stu-id="f1767-117">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="f1767-118">Pour plus d’informations, consultez [Guide pratique pour lire des fichiers texte avec plusieurs formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="f1767-118">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1767-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1767-119">See also</span></span>  
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

