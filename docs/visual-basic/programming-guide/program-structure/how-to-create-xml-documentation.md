---
title: "Comment : créer une Documentation XML en Visual Basic | Documents Microsoft"
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
- XML comments
- XML documentation, creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: 17
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 3171877f4fa1913b5535d71d671cea97b5a22850
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="495ec-102">Comment : créer une documentation XML en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="495ec-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="495ec-103">Cet exemple montre comment ajouter des commentaires de documentation XML à votre code.</span><span class="sxs-lookup"><span data-stu-id="495ec-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="495ec-104">Pour créer une documentation XML pour un type ou membre</span><span class="sxs-lookup"><span data-stu-id="495ec-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="495ec-105">Dans le **éditeur de Code**, positionnez votre curseur sur la ligne au-dessus du type ou du membre pour lequel vous souhaitez créer la documentation.</span><span class="sxs-lookup"><span data-stu-id="495ec-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="495ec-106">Type `'''` (trois guillemets simples).</span><span class="sxs-lookup"><span data-stu-id="495ec-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="495ec-107">Une structure XML pour le type ou le membre est ajoutée dans le **éditeur de Code**.</span><span class="sxs-lookup"><span data-stu-id="495ec-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="495ec-108">Ajout d’informations descriptives entre les balises appropriées.</span><span class="sxs-lookup"><span data-stu-id="495ec-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="495ec-109">Si vous ajoutez des lignes supplémentaires dans le bloc de documentation XML, chaque ligne doit commencer par `'''`.</span><span class="sxs-lookup"><span data-stu-id="495ec-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="495ec-110">Ajouter du code qui utilise le type ou le membre avec les nouveaux commentaires de documentation XML.</span><span class="sxs-lookup"><span data-stu-id="495ec-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="495ec-111">IntelliSense affiche le texte de la \<résumé > balise pour le type ou membre.</span><span class="sxs-lookup"><span data-stu-id="495ec-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="495ec-112">Compilez le code pour générer un fichier XML contenant les commentaires de documentation.</span><span class="sxs-lookup"><span data-stu-id="495ec-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="495ec-113">Pour plus d’informations, consultez [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="495ec-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="495ec-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="495ec-114">See Also</span></span>  
 <span data-ttu-id="495ec-115">[Documenter votre Code avec XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span><span class="sxs-lookup"><span data-stu-id="495ec-115">[Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md) </span></span>  
<span data-ttu-id="495ec-116"> [Balises de commentaire XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="495ec-116"> [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span></span>  
<span data-ttu-id="495ec-117"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)</span><span class="sxs-lookup"><span data-stu-id="495ec-117"> [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)</span></span>
