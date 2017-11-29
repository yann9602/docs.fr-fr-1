---
title: "Entités de caractères XML et XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
caps.latest.revision: "23"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5973c67b26e07bba69383cc625ff34493d825a41
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-character-entities-and-xaml"></a><span data-ttu-id="36952-102">Entités de caractères XML et XAML</span><span class="sxs-lookup"><span data-stu-id="36952-102">XML Character Entities and XAML</span></span>
<span data-ttu-id="36952-103">XAML utilise des entités de caractères définies en XML pour les caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="36952-103">XAML uses character entities defined in XML for special characters.</span></span> <span data-ttu-id="36952-104">Cette rubrique décrit des entités de caractères spécifiques et les considérations générales pour d'autres concepts XML en XAML.</span><span class="sxs-lookup"><span data-stu-id="36952-104">This topic describes some specific character entities and general considerations for other XML concepts in XAML.</span></span>  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a><span data-ttu-id="36952-105">Entités de caractères et problèmes d'échappement propres à XAML</span><span class="sxs-lookup"><span data-stu-id="36952-105">Character Entities and Escaping Issues That Are Unique to XAML</span></span>  
 <span data-ttu-id="36952-106">Le balisage XAML utilise généralement les mêmes entités de caractères et séquences d'échappement que celles définies en XML.</span><span class="sxs-lookup"><span data-stu-id="36952-106">XAML markup typically uses the same character entities and escape sequences that are defined in XML.</span></span>  
  
 <span data-ttu-id="36952-107">La principale exception réside dans le fait que les accolades ({ et }) ont de l’importance en XAML car ces caractères informent un processeur XAML qu’une séquence de caractères comprise entre les accolades doit être interprétée comme une extension du balisage.</span><span class="sxs-lookup"><span data-stu-id="36952-107">The main exception is that braces ({ and }) have significance in XAML because these characters inform a XAML processor that a character sequence enclosed by braces must be interpreted as a markup extension.</span></span> <span data-ttu-id="36952-108">Pour plus d’informations sur les extensions de balisage, consultez [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="36952-108">For more information about markup extensions, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
 <span data-ttu-id="36952-109">Toutefois, vous pouvez toujours afficher les accolades comme des caractères littéraux en utilisant une séquence d'échappement propre à XAML plutôt qu'à XML.</span><span class="sxs-lookup"><span data-stu-id="36952-109">However, you can still display the braces as literal characters by using an escape sequence that is particular to XAML instead of XML.</span></span> <span data-ttu-id="36952-110">Pour plus d’informations, consultez [{} séquence d’échappement - Extension de balisage](escape-sequence-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="36952-110">For more information, see [{} Escape Sequence - Markup Extension](escape-sequence-markup-extension.md).</span></span>  
  
 <span data-ttu-id="36952-111">Notez qu’une barre oblique inverse (\\) ne nécessite pas une séquence d’échappement lorsqu’elle est traitée en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="36952-111">Note that a backslash (\\) does not require an escape sequence when it is handled as a string.</span></span>  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a><span data-ttu-id="36952-112">Entités de caractères XML</span><span class="sxs-lookup"><span data-stu-id="36952-112">XML Character Entities</span></span>  
 <span data-ttu-id="36952-113">Comme indiqué précédemment, la plupart des entités de caractères et des séquences d'échappement qui sont généralement utilisées pour écrire le balisage XAML sont définies par XML.</span><span class="sxs-lookup"><span data-stu-id="36952-113">As mentioned previously, most character entities and escape sequences that are typically used to write XAML markup are defined by XML.</span></span> <span data-ttu-id="36952-114">Cette rubrique ne présente pas l'intégralité de ces entités ; vous trouverez de nombreuses autres références détaillées des entités dans la documentation externe, par exemple les spécifications XML.</span><span class="sxs-lookup"><span data-stu-id="36952-114">This topic does not provide the complete list of these entities; a detailed reference for the entities can be found in external documentation, such as in XML specifications.</span></span> <span data-ttu-id="36952-115">Toutefois, pour plus de commodité, cette rubrique présente certaines des entités de caractères XML spécifiques qui sont généralement utilisées dans le balisage XAML.</span><span class="sxs-lookup"><span data-stu-id="36952-115">However, for convenience, this topic lists some of the specific XML character entities that are typically used in XAML markup.</span></span>  
  
|<span data-ttu-id="36952-116">Caractère</span><span class="sxs-lookup"><span data-stu-id="36952-116">Character</span></span>|<span data-ttu-id="36952-117">Entité</span><span class="sxs-lookup"><span data-stu-id="36952-117">Entity</span></span>|<span data-ttu-id="36952-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="36952-118">Notes</span></span>|  
|---------------|------------|-----------|  
|<span data-ttu-id="36952-119">& (et commercial)</span><span class="sxs-lookup"><span data-stu-id="36952-119">& (ampersand)</span></span>|&amp;|<span data-ttu-id="36952-120">Doit être utilisé à la fois pour les valeurs d'attribut et pour le contenu d'un élément.</span><span class="sxs-lookup"><span data-stu-id="36952-120">Must be used both for attribute values and for content of an element.</span></span>|  
|<span data-ttu-id="36952-121">> (supérieur à)</span><span class="sxs-lookup"><span data-stu-id="36952-121">> (greater-than character)</span></span>|&gt;|<span data-ttu-id="36952-122">Doit être utilisé pour la valeur d'attribut, mais le caractère > est acceptable comme contenu d'un élément à condition que le caractère < ne le précède pas.</span><span class="sxs-lookup"><span data-stu-id="36952-122">Must be used for an attribute value, but > is acceptable as the content of an element as long as < does not precede it.</span></span>|  
|<span data-ttu-id="36952-123">< (inférieur à)</span><span class="sxs-lookup"><span data-stu-id="36952-123">< (less-than character)</span></span>|&lt;|<span data-ttu-id="36952-124">Doit être utilisé pour une valeur d’attribut, mais \< est acceptable comme contenu d’un élément en tant que > ne le suive pas.</span><span class="sxs-lookup"><span data-stu-id="36952-124">Must be used for an attribute value, but \< is acceptable as the content of an element as long as > does not follow it.</span></span>|  
|<span data-ttu-id="36952-125">" (guillemets droits)</span><span class="sxs-lookup"><span data-stu-id="36952-125">" (straight quotation mark)</span></span>|&quot;|<span data-ttu-id="36952-126">Doit être utilisé pour une valeur d'attribut, mais le guillemet droit (") est acceptable comme contenu d'un élément.</span><span class="sxs-lookup"><span data-stu-id="36952-126">Must be used for an attribute value, but a straight quotation mark (") is acceptable as the content of an element.</span></span> <span data-ttu-id="36952-127">Notez que les valeurs d'attributs peuvent être placées entre un guillemet droit unique (') ou des guillemets droit (") ; le caractère qui apparaît en premier définit ce qui est inclus dans la valeur d'attribut, et l'autre guillemet peut ensuite être utilisé comme littéral dans la valeur.</span><span class="sxs-lookup"><span data-stu-id="36952-127">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="36952-128">' (guillemet droit unique)</span><span class="sxs-lookup"><span data-stu-id="36952-128">' (single straight quotation mark)</span></span>|&apos;|<span data-ttu-id="36952-129">Doit être utilisé pour une valeur d'attribut, mais le guillemet droit unique (') est acceptable comme contenu d'un élément.</span><span class="sxs-lookup"><span data-stu-id="36952-129">Must be used for an attribute value, but a single straight quotation mark (') is acceptable as the content of an element.</span></span> <span data-ttu-id="36952-130">Notez que les valeurs d'attributs peuvent être placées entre un guillemet droit unique (') ou des guillemets droit (") ; le caractère qui apparaît en premier définit ce qui est inclus dans la valeur d'attribut, et l'autre guillemet peut ensuite être utilisé comme littéral dans la valeur.</span><span class="sxs-lookup"><span data-stu-id="36952-130">Note that attribute values may be enclosed either by a single straight quotation mark (') or by a straight quotation mark ("); whichever character appears first defines the attribute value enclosure, and the alternative quote can then be used as a literal within the value.</span></span>|  
|<span data-ttu-id="36952-131">(mappages de caractères numériques)</span><span class="sxs-lookup"><span data-stu-id="36952-131">(numeric character mappings)</span></span>|<span data-ttu-id="36952-132">&#*[entier]* ; ou & #x*[hex]*;</span><span class="sxs-lookup"><span data-stu-id="36952-132">&#*[integer]*; or &#x*[hex]*;</span></span>|<span data-ttu-id="36952-133">XAML prend en charge les mappages de caractères numériques dans de l'encodage actif.</span><span class="sxs-lookup"><span data-stu-id="36952-133">XAML supports numeric character mappings into the encoding that is active.</span></span>|  
|<span data-ttu-id="36952-134">(espace insécable)</span><span class="sxs-lookup"><span data-stu-id="36952-134">(nonbreaking space)</span></span>|<span data-ttu-id="36952-135">&\#160 ; (en supposant que l’encodage UTF-8)</span><span class="sxs-lookup"><span data-stu-id="36952-135">&\#160; (assuming UTF-8 encoding)</span></span>|<span data-ttu-id="36952-136">Pour les éléments de document dynamique ou les éléments qui acceptent du texte tels que le <xref:System.Windows.Controls.TextBox> WPF, les espaces insécables ne sont pas normalisés hors du balisage, même pour `xml:space="default"`.</span><span class="sxs-lookup"><span data-stu-id="36952-136">For flow document elements, or elements that take text such as the WPF <xref:System.Windows.Controls.TextBox>, nonbreaking spaces are not normalized out of the markup, even for `xml:space="default"`.</span></span> <span data-ttu-id="36952-137">(Pour plus d’informations, consultez [traitement des espaces blancs en XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span><span class="sxs-lookup"><span data-stu-id="36952-137">(For more information, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).)</span></span>|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a><span data-ttu-id="36952-138">Format de commentaire XML</span><span class="sxs-lookup"><span data-stu-id="36952-138">XML Comment Format</span></span>  
 <span data-ttu-id="36952-139">XAML utilise le format de commentaire XML : le début du commentaire est `<!--`, la fin du commentaire est `-->,` et la séquence `--` ne doit pas se produire dans un commentaire.</span><span class="sxs-lookup"><span data-stu-id="36952-139">XAML uses the XML comment format: the start of the comment is `<!--`, the end of comment is `-->,` and the sequence `--` must not occur within the comment.</span></span>  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a><span data-ttu-id="36952-140">Instructions de traitement XML</span><span class="sxs-lookup"><span data-stu-id="36952-140">XML Processing Instructions</span></span>  
 <span data-ttu-id="36952-141">XAML gère les instructions de traitement XML conformément aux spécifications XML, qui déclarent que les instructions doivent être transmises.</span><span class="sxs-lookup"><span data-stu-id="36952-141">XAML handles XML processing instructions according to XML specifications, which state that the instructions must be passed through.</span></span> <span data-ttu-id="36952-142">Traitement XAML dans les Services XAML .NET Framework n’utilise pas les instructions de traitement.</span><span class="sxs-lookup"><span data-stu-id="36952-142">XAML processing in .NET Framework XAML Services  does not use any processing instructions.</span></span> <span data-ttu-id="36952-143">Les autres infrastructures existantes qui utilisent XAML n'utilisent pas non plus d'instructions de traitement de XAML.</span><span class="sxs-lookup"><span data-stu-id="36952-143">Other existing frameworks that use XAML also do not use processing instructions from XAML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36952-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36952-144">See Also</span></span>  
 [<span data-ttu-id="36952-145">Vue d’ensemble du langage XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="36952-145">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="36952-146">Extensions de balisage et XAML WPF</span><span class="sxs-lookup"><span data-stu-id="36952-146">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="36952-147">XamlName, grammaire</span><span class="sxs-lookup"><span data-stu-id="36952-147">XamlName Grammar</span></span>](../../../docs/framework/xaml-services/xamlname-grammar.md)  
 [<span data-ttu-id="36952-148">Traitement des espaces blancs en XAML</span><span class="sxs-lookup"><span data-stu-id="36952-148">Whitespace Processing in XAML</span></span>](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
