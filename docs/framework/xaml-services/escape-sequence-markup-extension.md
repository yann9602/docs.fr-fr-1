---
title: "{}, Séquence d’échappement - Extension de balisage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: "21"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: befbf9960afffcd30bc96863dcc00b4acad2c21a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="-escape-sequence--markup-extension"></a><span data-ttu-id="7d4cc-102">{}, séquence d’échappement/extension de balisage</span><span class="sxs-lookup"><span data-stu-id="7d4cc-102">{} Escape Sequence / Markup Extension</span></span>
<span data-ttu-id="7d4cc-103">Fournit la séquence d’échappement XAML pour les valeurs d’attribut.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-103">Provides the XAML escape sequence for attribute values.</span></span> <span data-ttu-id="7d4cc-104">La séquence d’échappement autorise les valeurs suivantes dans l’attribut doit être interprété comme un littéral.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-104">The escape sequence allows the subsequent values in the attribute to be interpreted as a literal.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="7d4cc-105">Utilisation d'attributs XAML</span><span class="sxs-lookup"><span data-stu-id="7d4cc-105">XAML Attribute Usage</span></span>  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a><span data-ttu-id="7d4cc-106">Utilisation des éléments de propriété XAML</span><span class="sxs-lookup"><span data-stu-id="7d4cc-106">XAML Property Element Usage</span></span>  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="7d4cc-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="7d4cc-107">XAML Values</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d4cc-108">*literalValue*</span><span class="sxs-lookup"><span data-stu-id="7d4cc-108">*literalValue*</span></span>|<span data-ttu-id="7d4cc-109">La chaîne littérale qui suit la séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-109">The literal string that follows the escape sequence.</span></span> <span data-ttu-id="7d4cc-110">En général, cette chaîne contient une accolade ouvrante ou fermante ({ou}).</span><span class="sxs-lookup"><span data-stu-id="7d4cc-110">Typically this string contains an open or close brace ({ or }).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d4cc-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="7d4cc-111">Remarks</span></span>  
 <span data-ttu-id="7d4cc-112">La séquence d’échappement ({}) est utilisée afin qu’une accolade ouvrante ({}) peut être utilisée comme un caractère littéral dans XAML.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-112">The escape sequence ({}) is used so that an open brace ({)can be used as a literal character in XAML.</span></span>  
  
 <span data-ttu-id="7d4cc-113">Lecteurs XAML utilisent en général l’accolade ouvrante ({}) pour indiquer le point d’entrée d’une extension de balisage ; toutefois, ils vérifient d’abord le caractère suivant pour déterminer s’il s’agit d’une accolade fermante (}).</span><span class="sxs-lookup"><span data-stu-id="7d4cc-113">XAML readers typically use the open brace ({) to denote the entry point of a markup extension; however, they first check the next character to determine whether it is a closing brace (}).</span></span> <span data-ttu-id="7d4cc-114">Uniquement lorsque les deux accolades ({}) sont adjacentes, sont elles considérées comme une séquence d’échappement.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-114">Only when the two braces ({}) are adjacent, are they considered an escape sequence.</span></span>  
  
 <span data-ttu-id="7d4cc-115">Si la séquence d’échappement est rencontrée, le lecteur XAML doit traiter le reste de la chaîne en tant que chaîne.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-115">If the escape sequence is encountered, the XAML reader should process the remainder of the string as a string.</span></span> <span data-ttu-id="7d4cc-116">Toutefois, si la séquence d’échappement est appliquée à un membre qui a un convertisseur de type, la chaîne peut subir une conversion de type lorsqu’il est interprété par un writer XAML.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-116">However, if the escape sequence is applied to a member that has a type converter, the string might undergo type conversion when it is interpreted by a XAML writer.</span></span>  
  
 <span data-ttu-id="7d4cc-117">La séquence d’échappement n’est pas une extension de balisage et n’est pas sauvegardée par une classe.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-117">The escape sequence is not a markup extension and is not backed by a class.</span></span> <span data-ttu-id="7d4cc-118">Toutefois, il est une convention qui doivent respecter les lecteurs XAML (y compris les lecteurs XAML personnalisés).</span><span class="sxs-lookup"><span data-stu-id="7d4cc-118">However, it is a convention that XAML readers (including custom XAML readers) should respect.</span></span>  
  
 <span data-ttu-id="7d4cc-119">Un guillemet (") ne peut pas être utilisé comme une séquence d’échappement de cette manière.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-119">A quotation mark (") cannot be used as an escape sequence in this manner.</span></span> <span data-ttu-id="7d4cc-120">Si vous devez définir un guillemet comme une valeur de propriété pour une propriété de non-contenu, utilisez la syntaxe d’élément de propriété et placez le guillemet comme une chaîne à l’intérieur de l’élément de propriété ou utilisez une entité de caractère XML.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-120">If you need to set a quotation mark as a property value for a noncontent property, use property element syntax and place the quotation mark as a string inside the property element, or use an XML character entity.</span></span> <span data-ttu-id="7d4cc-121">Pour une propriété de contenu, le guillemet peut être l’ensemble du contenu.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-121">For a content property, the quotation mark can be the entire content.</span></span>  
  
 <span data-ttu-id="7d4cc-122">La séquence d’échappement ({}) est souvent nécessaire lors de la spécification d’un type XML qui doit inclure un qualificateur d’espace de noms dans un emplacement où une extension de balisage XAML peut apparaître.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-122">The escape sequence ({}) is frequently required when specifying an XML type that must include a namespace qualifier in a location where a XAML markup extension might appear.</span></span> <span data-ttu-id="7d4cc-123">Cela inclut le début d’une valeur d’attribut XAML et dans une extension de balisage, immédiatement après un signe égal (=).</span><span class="sxs-lookup"><span data-stu-id="7d4cc-123">This includes the start of a XAML attribute value, and in a markup extension, immediately after an equal sign (=).</span></span> <span data-ttu-id="7d4cc-124">L’exemple suivant montre des séquences d’échappement pour un espace de noms XML qui apparaît au début d’une valeur d’attribut XAML.</span><span class="sxs-lookup"><span data-stu-id="7d4cc-124">The following example shows escape sequences for an XML namespace that appears at the start of a XAML attribute value.</span></span>  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a><span data-ttu-id="7d4cc-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d4cc-125">See Also</span></span>  
 [<span data-ttu-id="7d4cc-126">Convertisseurs de types et extensions de balisage pour XAML</span><span class="sxs-lookup"><span data-stu-id="7d4cc-126">Type Converters and Markup Extensions for XAML</span></span>](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [<span data-ttu-id="7d4cc-127">Entités de caractères XML et XAML</span><span class="sxs-lookup"><span data-stu-id="7d4cc-127">XML Character Entities and XAML</span></span>](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
