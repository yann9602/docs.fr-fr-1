---
title: XamlName, grammaire
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
caps.latest.revision: "13"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 92327c8ff6232e64bf8b6b2a9d78e4a9eb30f3e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="xamlname-grammar"></a>XamlName, grammaire
XamlName, grammaire est une grammaire spécifique qui est définie dans la spécification du langage XAML [MS-XAML], reproduite ici par commodité.  
  
## <a name="from-the-xaml-specification"></a>À partir de la spécification de XAML  
 La spécification [MS-XAML] définit la grammaire XamlName pour identifier le jeu d’identificateurs symboliques légaux utilisé pour les types et propriétés.  
  
 Valeurs de chaîne qui sont de type que XamlName doivent se conformer à la grammaire suivante :  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Qui suppose que les valeurs de catégorie générale suivantes comme défini dans la base de données de caractères Unicode  
  
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
  
 Code XAML définit une deuxième grammaire, DottedXamlName, qui est utilisé pour la propriété et événement références qualifiées et également pour les membres attachés. Pour plus d’informations, consultez <xref:System.Windows.DependencyProperty> et [vue d’ensemble du XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
 Valeurs de chaîne qui sont de type que DottedXamlName doivent se conformer à la grammaire suivante :  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Remarques  
 Pour la spécification complète, consultez [ \[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).
