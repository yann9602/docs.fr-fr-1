---
title: Guide pratique pour convertir du RTF en texte brut (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], converting from RTF
ms.assetid: 3b386a87-899d-4d98-bc82-a980526ddaac
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e4c7b48467f3b260526c604fa3a36fc5d80374e
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-rtf-to-plain-text-c-programming-guide"></a><span data-ttu-id="682b2-102">Guide pratique pour convertir du RTF en texte brut (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="682b2-102">How to: Convert RTF to Plain Text (C# Programming Guide)</span></span>
<span data-ttu-id="682b2-103">Le format RTF (Rich Text Format) est un format de document développé par Microsoft à la fin des années 1980 pour permettre l’échange de documents entre les systèmes d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="682b2-103">Rich Text Format (RTF) is a document format developed by Microsoft in the late 1980s to enable the exchange of documents across operating systems.</span></span> <span data-ttu-id="682b2-104">Microsoft Word et WordPad peuvent tous les deux lire et écrire des documents RTF.</span><span class="sxs-lookup"><span data-stu-id="682b2-104">Both Microsoft Word and WordPad can read and write RTF documents.</span></span> <span data-ttu-id="682b2-105">Dans le .NET Framework, vous pouvez utiliser le contrôle <xref:System.Windows.Forms.RichTextBox> pour créer un traitement de texte qui prend en charge le format RTF et permet à un utilisateur d’appliquer une mise en forme de type WYSIWYG au texte.</span><span class="sxs-lookup"><span data-stu-id="682b2-105">In the .NET Framework, you can use the <xref:System.Windows.Forms.RichTextBox> control to create a word processor that supports RTF and enables a user to apply formatting to text in a WYSIWIG manner.</span></span>  
  
 <span data-ttu-id="682b2-106">Vous pouvez également utiliser le contrôle <xref:System.Windows.Forms.RichTextBox> pour supprimer par programmation les codes de mise en forme RTF d’un document et le convertir en texte brut.</span><span class="sxs-lookup"><span data-stu-id="682b2-106">You can also use the <xref:System.Windows.Forms.RichTextBox> control to programmatically remove the RTF formatting codes from a document and convert it to plain text.</span></span> <span data-ttu-id="682b2-107">Vous n’avez pas besoin d’incorporer le contrôle dans un Windows Form pour effectuer ce type d’opération.</span><span class="sxs-lookup"><span data-stu-id="682b2-107">You do not need to embed the control in a Windows Form to perform this kind of operation.</span></span>  
  
### <a name="to-use-the-richtextbox-control-in-a-project"></a><span data-ttu-id="682b2-108">Pour utiliser le contrôle RichTextBox dans un projet</span><span class="sxs-lookup"><span data-stu-id="682b2-108">To use the RichTextBox control in a project</span></span>  
  
1.  <span data-ttu-id="682b2-109">Ajoutez une référence à System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="682b2-109">Add a reference to System.Windows.Forms.dll.</span></span>  
  
2.  <span data-ttu-id="682b2-110">Ajoutez une directive using pour l’espace de noms `System.Windows.Forms` (facultatif).</span><span class="sxs-lookup"><span data-stu-id="682b2-110">Add a using directive for the `System.Windows.Forms` namespace (optional).</span></span>  
  
## <a name="example"></a><span data-ttu-id="682b2-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="682b2-111">Example</span></span>  
 <span data-ttu-id="682b2-112">L’exemple suivant convertit un exemple de fichier RTF en texte brut.</span><span class="sxs-lookup"><span data-stu-id="682b2-112">The following example converts a sample RTF file to plain text.</span></span> <span data-ttu-id="682b2-113">Le fichier contient la mise en forme RTF (comme les informations de police), quatre caractères Unicode et quatre caractères ASCII étendus.</span><span class="sxs-lookup"><span data-stu-id="682b2-113">The file contains RTF formatting (such as font information), four Unicode characters, and four extended ASCII characters.</span></span> <span data-ttu-id="682b2-114">L’exemple de code ouvre le fichier, transmet son contenu à un <xref:System.Windows.Forms.RichTextBox> au format RTF, récupère le contenu sous forme de texte, affiche le texte dans un <xref:System.Windows.Forms.MessageBox>, puis affiche le texte dans un fichier au format UTF-8.</span><span class="sxs-lookup"><span data-stu-id="682b2-114">The example code opens the file, passes its content to a <xref:System.Windows.Forms.RichTextBox> as RTF, retrieves the content as text, displays the text in a <xref:System.Windows.Forms.MessageBox>, and outputs the text to a file in UTF-8 format.</span></span>  
  
 <span data-ttu-id="682b2-115">`MessageBox` et le fichier de sortie contiennent le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="682b2-115">The `MessageBox` and the output file contain the following text:</span></span>  
  
```  
The Greek word for "psyche" is spelled ψυχή. The Greek letters are encoded in Unicode.  
These characters are from the extended ASCII character set (Windows code page 1252):  âäӑå  
```  
  
 <span data-ttu-id="682b2-116">[!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="682b2-116">[!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]</span></span>  
  
 <span data-ttu-id="682b2-117">Les caractères RTF sont encodés dans huit bits.</span><span class="sxs-lookup"><span data-stu-id="682b2-117">RTF characters are encoded in eight bits.</span></span> <span data-ttu-id="682b2-118">Toutefois, les utilisateurs peuvent spécifier des caractères Unicode en plus de les caractères étendus ASCII des pages de codes spécifiées.</span><span class="sxs-lookup"><span data-stu-id="682b2-118">However, users can specify Unicode characters in addition to extended ASCII characters from specified code pages.</span></span> <span data-ttu-id="682b2-119">Étant donné que la propriété <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> est de type [string](../../../csharp/language-reference/keywords/string.md), les caractères sont encodés au format Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="682b2-119">Because the <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> property is of type [string](../../../csharp/language-reference/keywords/string.md), the characters are encoded as Unicode UTF-16.</span></span> <span data-ttu-id="682b2-120">Les caractères ASCII étendus et les caractères Unicode du document RTF source sont encodés correctement dans la sortie de texte.</span><span class="sxs-lookup"><span data-stu-id="682b2-120">Any extended ASCII characters and Unicode characters from the source RTF document are correctly encoded in the text output.</span></span>  
  
 <span data-ttu-id="682b2-121">Si vous utilisez la méthode <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> pour écrire le texte sur le disque, le texte doit être encodé au format UTF-8 (sans marque d’ordre d’octet).</span><span class="sxs-lookup"><span data-stu-id="682b2-121">If you use the <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> method to write the text to disk, the text will be encoded as UTF-8 (without a Byte Order Mark).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="682b2-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="682b2-122">See Also</span></span>  
 <span data-ttu-id="682b2-123"><xref:System.Windows.Forms.RichTextBox?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="682b2-123"><xref:System.Windows.Forms.RichTextBox?displayProperty=fullName></span></span>   
 [<span data-ttu-id="682b2-124">Chaînes</span><span class="sxs-lookup"><span data-stu-id="682b2-124">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

