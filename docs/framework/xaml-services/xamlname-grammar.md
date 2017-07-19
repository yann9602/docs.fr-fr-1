---
title: "XamlName, grammaire | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DottedXamlName (grammaire) (services XAML)"
  - "grammaire (services XAML), DottedXamlName"
  - "grammaire (services XAML), XamlName"
  - "noms en XAML (services XAML)"
  - "XamlName (grammaire) (services XAML)"
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
caps.latest.revision: 13
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 13
---
# XamlName, grammaire
La grammaire XamlName est une grammaire spécifique définie dans la spécification du langage \[MS\-XAML\], reproduite ici par commodité.  
  
## À partir de la spécification XAML  
 La spécification \[MLLE\-XAML\] définit la grammaire XamlName pour identifier le jeu d'identificateurs symboliques légaux utilisé pour les types et les propriétés.  
  
 Les valeurs de chaîne du type XamlName doivent se conformer à la grammaire suivante :  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
  
```  
  
 Cette grammaire suppose les valeurs de catégorie générale suivantes telles que définies dans Unicode Character Database  
  
```  
  
Lu  
Letter, Uppercase  
Ll  
Letter, Lowercase  
Lt  
Letter, Titlecase  
Lm  
Letter, Modifier  
Lo  
Letter, Other  
Mn  
Mark, Non-Spacing  
Mc  
Mark, Spacing Combining  
Nd  
Number, Decimal  
Nl  
Number, Letter  
```  
  
 Le langage XAML définit une deuxième grammaire, DottedXamlName, utilisée pour les références qualifiées de propriété et d'événement, ainsi que pour les membres attachés.  Pour plus d'informations, consultez <xref:System.Windows.DependencyProperty> et [Vue d'ensemble du langage XAML \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
 Les valeurs de chaîne du type DottedXamlName doivent se conformer à la grammaire suivante :  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## Notes  
 Pour la spécification complète, consultez [\[MS\-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).