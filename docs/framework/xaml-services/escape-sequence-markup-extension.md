---
title: "{} Escape Sequence / Markup Extension | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "{}"
helpviewer_keywords: 
  - "XAML [XAML Services], quotation mark (")"
  - "{} escape sequence [XAML Services]"
  - "XAML [XAML Services], {} escape sequence"
  - "XAML [XAML Services], escape sequence"
  - "quotation mark (") [XAML Services]"
  - "escape sequence [XAML Services]"
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: 21
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
---
# {} Escape Sequence / Markup Extension
Fournit la séquence d'échappement XAML pour les valeurs d'attribut.  La séquence d'échappement permet aux valeurs suivantes dans l'attribut d'être interprétées en tant que littéral.  
  
## Utilisation d'attributs XAML  
  
```  
<object property="{} literalValue" .../>  
```  
  
## Utilisation des éléments de propriété XAML  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|*literalValue*|La chaîne littérale qui suit la séquence d'échappement.  En général, cette chaîne contient une accolade ouvrante ou fermante \({ ou }\).|  
  
## Notes  
 La séquence d'échappement \({}\) est utilisée afin qu'une accolade ouvrante \({\) puisse être utilisé en tant que caractère littéral dans XAML.  
  
 Les lecteurs XAML utilisent en général l'accolade ouvrante \({\) pour désigner le point d'entrée d'une extension de balisage ; toutefois, ils vérifient d'abord le caractère suivant pour déterminer s'il s'agit d'une accolade fermante \(}\).  Seules les deux accolades \({}\) sont adjacentes,car elles sont considérées comme une séquence d'échappement.  
  
 Si la séquence d'échappement est rencontrée, le lecteur XAML doit traiter le reste de la chaîne en tant que chaîne.  Toutefois, si la séquence d'échappement est appliquée à un membre qui a un convertisseur de type, la chaîne peut subir une conversion de type lorsqu'elle est interprétée par un enregistreur XAML.  
  
 La séquence d'échappement n'est pas une extension de balisage et n'est pas stockée par une classe.  Toutefois, il s'agit d'une convention que les lecteurs XAML \(lecteurs XAML personnalisés inclus\) doivent respecter.  
  
 Un guillemet \("\) ne peut pas être utilisé comme séquence d'échappement de cette manière.  Si vous devez définir un guillemet comme une valeur de propriété pour une propriété de non\-contenu, utilisez la syntaxe d'élément de propriété et placez le guillemet comme une chaîne à l'intérieur de l'élément de propriété, ou utilisez une entité de caractère XML.  Pour une propriété de contenu, le guillemet peut être le contenu entier.  
  
 La séquence d'échappement \({}\) est fréquemment requise lors de la spécification d'un type XML qui doit inclure un qualificateur d'espace de noms dans un emplacement où l'extension de balise XAML peut apparaître,  Cela inclut le début d'une valeur d'attribut XAML, et dans une extension de balisage, juste après le signe égal \(\=\).  L'exemple suivant montre des séquences d'échappements pour un espace de noms XML qui apparaît au début d'une valeur d'attribut XAML.  
  
 [!code-xml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## Voir aussi  
 [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)   
 [XML Character Entities and XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)