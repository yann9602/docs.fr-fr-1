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
ms.workload: dotnet
ms.openlocfilehash: 47a2d72ea9558003412cc3773e26fb5be751fa19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
  
## <a name="remarks"></a>Notes  
 Pour la spécification complète, consultez [ \[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).
