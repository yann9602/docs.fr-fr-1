---
title: "XML Character Entities and XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "&"
  - "&amp"
  - "&gt"
  - "&lt"
helpviewer_keywords: 
  - "XAML [XAML Services], special characters"
  - "ampersand (&) [XAML Services]"
  - "special characters [XAML Services]"
  - "apostrophe (') [XAML Services]"
  - "greater-than (>) character [XAML Services]"
  - "XAML [XAML Services], quotation mark (")"
  - "XAML [XAML Services], apostrophe (')"
  - "& (ampersand) [XAML Services]"
  - "XAML [XAML Services], & (ampersand)"
  - "XAML [XAML Services], escape sequence"
  - "quotation mark (") [XAML Services]"
  - "less-than (<) character [XAML Services]"
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
caps.latest.revision: 23
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 21
---
# XML Character Entities and XAML
XAML utilise des entités de caractères définies en XML pour les caractères spéciaux.  Cette rubrique décrit des entités de caractères spécifiques et les considérations générales pour d'autres concepts XML en XAML.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## Entités de caractères et problèmes d'échappement propres à XAML  
 Le balisage XAML utilise généralement les mêmes entités de caractères et séquences d'échappement que celles définies en XML.  
  
 La principale exception réside dans le fait que les accolades \({ et }\) ont de l'importance en XAML car ces caractères informent un processeur XAML qu'une séquence de caractères comprise entre les accolades doit être interprétée comme une extension du balisage.  Pour plus d'informations sur les extensions de balisage, consultez [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
 Toutefois, vous pouvez toujours afficher les accolades comme des caractères littéraux en utilisant une séquence d'échappement propre à XAML plutôt qu'à XML.  Pour plus d'informations, consultez [{} Escape Sequence \/ Markup Extension](../../../docs/framework/xaml-services/escape-sequence-markup-extension.md).  
  
 Notez qu'une barre oblique inverse \(\\\) ne requiert pas de séquence d'échappement lorsqu'elle est traitée en tant que chaîne.  
  
<a name="xml_character_entities"></a>   
## Entités de caractères XML  
 Comme indiqué précédemment, la plupart des entités de caractères et des séquences d'échappement qui sont généralement utilisées pour écrire le balisage XAML sont définies par XML.  Cette rubrique ne présente pas l'intégralité de ces entités ; vous trouverez de nombreuses autres références détaillées des entités dans la documentation externe, par exemple les spécifications XML.  Toutefois, pour plus de commodité, cette rubrique présente certaines des entités de caractères XML spécifiques qui sont généralement utilisées dans le balisage XAML.  
  
|Caractère|Entité|Remarques|  
|---------------|------------|---------------|  
|& \(et commercial\)|&amp;|Doit être utilisé à la fois pour les valeurs d'attribut et pour le contenu d'un élément.|  
|\> \(supérieur à\)|&gt;|Doit être utilisé pour la valeur d'attribut, mais le caractère \> est acceptable comme contenu d'un élément à condition que le caractère \< ne le précède pas.|  
|\< \(inférieur à\)|&lt;|Doit être utilisé pour la valeur d'attribut, mais le caractère \< est acceptable comme contenu d'un élément à condition que le caractère \> ne le suive pas.|  
|" \(guillemets droits\)|&quot;|Doit être utilisé pour une valeur d'attribut, mais le guillemet droit \("\) est acceptable comme contenu d'un élément.  Notez que les valeurs d'attributs peuvent être placées entre un guillemet droit unique \('\) ou des guillemets droit \("\) ; le caractère qui apparaît en premier définit ce qui est inclus dans la valeur d'attribut, et l'autre guillemet peut ensuite être utilisé comme littéral dans la valeur.|  
|' \(guillemet droit unique\)|&apos;|Doit être utilisé pour une valeur d'attribut, mais le guillemet droit unique \('\) est acceptable comme contenu d'un élément.  Notez que les valeurs d'attributs peuvent être placées entre un guillemet droit unique \('\) ou des guillemets droit \("\) ; le caractère qui apparaît en premier définit ce qui est inclus dans la valeur d'attribut, et l'autre guillemet peut ensuite être utilisé comme littéral dans la valeur.|  
|\(mappages de caractères numériques\)|&\#*\[entier\]*; ou &\#x*\[hexa\]*;|XAML prend en charge les mappages de caractères numériques dans de l'encodage actif.|  
|\(espace insécable\)|&\#160; \(à supposer que l'encodage UTF\-8 est utilisé\)|Pour les éléments de document dynamique ou les éléments qui acceptent du texte tels que le <xref:System.Windows.Controls.TextBox> WPF, les espaces insécables ne sont pas normalisés hors du balisage, même pour `xml:space="default"`.  \(Pour plus d'informations, consultez [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).\)|  
  
<a name="xml_comment_format"></a>   
## Format de commentaire XML  
 XAML utilise le format de commentaire XML : le début du commentaire est `<!--`, la fin du commentaire est `-->,` et la séquence `--` ne doit pas se produire dans un commentaire.  
  
<a name="xml_processing_instructions"></a>   
## Instructions de traitement XML  
 XAML gère les instructions de traitement XML conformément aux spécifications XML, qui déclarent que les instructions doivent être transmises.  Le traitement XAML des services XAML .NET Framework n'utilise pas d'instructions de traitement.  Les autres infrastructures existantes qui utilisent XAML n'utilisent pas non plus d'instructions de traitement de XAML.  
  
## Voir aussi  
 [{} Escape Sequence \/ Markup Extension](../../../docs/framework/xaml-services/escape-sequence-markup-extension.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Extensions de balisage et XAML WPF](../../../ocs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [XamlName, grammaire](../../../docs/framework/xaml-services/xamlname-grammar.md)   
 [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)