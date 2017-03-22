---
title: "Utilisation d’Expressions régulières avec le contrôle MaskedTextBox en Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 15d8f131aa834321fcf7e8ca633929385c666e6a
ms.lasthandoff: 03/13/2017

---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Utilisation d'expressions régulières avec le contrôle MaskedTextBox en Visual Basic
Cet exemple montre comment convertir des expressions régulières simples pour utiliser le <xref:System.Windows.Forms.MaskedTextBox>contrôle.</xref:System.Windows.Forms.MaskedTextBox>  
  
## <a name="description-of-the-masking-language"></a>Description de la langue de masques  
 La norme <xref:System.Windows.Forms.MaskedTextBox>le langage de masquage est basé sur celui utilisé par le `Masked Edit` contrôler dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 et doit être connu des utilisateurs qui migrent depuis cette plateforme.</xref:System.Windows.Forms.MaskedTextBox>  
  
 Le <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>propriété de la <xref:System.Windows.Forms.MaskedTextBox>contrôle spécifie le masque de saisie à utiliser.</xref:System.Windows.Forms.MaskedTextBox> </xref:System.Windows.Forms.MaskedTextBox.Mask%2A> Le masque doit être une chaîne composée d’un ou plusieurs des éléments de masquage dans le tableau suivant.  
  
|Élément de masquage|Description|Élément d’expression régulière|  
|---------------------|-----------------|--------------------------------|  
|0|Tout chiffre compris entre 0 et 9. Entrée obligatoire.|\d|  
|9|Chiffre ou espace. Entrée facultative.|[ \d]?|  
|#|Chiffre ou espace. Entrée facultative. Si cette position est vide dans le masque, il est rendu comme un espace. Signe plus (+) et moins (-), signes sont autorisés.|[ \d+-]?|  
|L|Lettres ASCII. Entrée obligatoire.|[a-zA-Z]|  
|?|Lettres ASCII. Entrée facultative.|[a-zA-Z] ?|  
|&|Caractère. Entrée obligatoire.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo]}|  
|C|Caractère. Entrée facultative.|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}] ?|  
|A|Alphanumérique. Entrée facultative.|\W|  
|.|Espace réservé décimal approprié à la culture.|Non disponible.|  
|,|Espace réservé aux milliers approprié à la culture.|Non disponible.|  
|:|Séparateur d’heure approprié à la culture.|Non disponible.|  
|/|Séparateur de date approprié à la culture.|Non disponible.|  
|$|Symbole de devise approprié à la culture.|Non disponible.|  
|\<|Convertit tous les caractères qui suivent en minuscules.|Non disponible.|  
|>|Convertit tous les caractères qui suivent en majuscules.|Non disponible.|  
|&#124;|Annule un décalage vers la précédente d’ou vers le bas.|Non disponible.|  
|\|Remplace un caractère de masque, transformant en un littéral. «\\\\» est la séquence d’échappement pour une barre oblique inverse.|\|  
|Tous les autres caractères.|Littéraux. Tous les éléments non masque apparaîtra eux-mêmes dans <xref:System.Windows.Forms.MaskedTextBox>.</xref:System.Windows.Forms.MaskedTextBox>|Tous les autres caractères.|  
  
 Le séparateur décimal (.) millièmes (), ( :), date (/) et heure devise ($) affichent par défaut les symboles comme défini par la culture de l’application. Vous pouvez les forcer à afficher les symboles d’une autre culture à l’aide de la <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>propriété.</xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>  
  
## <a name="regular-expressions-and-masks"></a>Expressions régulières et masques  
 Bien que vous pouvez utiliser des expressions régulières et masques pour valider l’entrée d’utilisateur, ils ne sont pas entièrement équivalentes. Expressions régulières peuvent exprimer des modèles plus complexes que les masques, mais les masques peuvent exprimer les mêmes informations plus succinctement et dans un format culturellement pertinent.  
  
 Le tableau suivant compare quatre expressions régulières et le masque équivalent pour chacune.  
  
|Expression régulière|Masque|Notes|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|Le `/` dans le masque est un séparateur de date logique, et il apparaît à l’utilisateur comme le séparateur de date approprié à la culture actuelle de l’application.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Date (jour, abréviation du mois et année) au format américain dans lequel l’abréviation à trois lettres du mois est affichée avec une lettre majuscule initiale suivie de deux lettres en minuscules.|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|Numéro de téléphone des États-Unis, indicatif régional facultatif. Si l’utilisateur ne souhaite pas entrer les caractères facultatifs, il peut entrer des espaces ou placer le pointeur de souris directement à la position représentée par le premier 0 dans le masque.|  
|`$\d{6}.00`|`$999,999.00`|Valeur monétaire comprise entre 0 et 999999. La devise, millième et caractères décimaux seront remplacés au moment de l’exécution par leurs équivalents spécifiques à la culture.|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A></xref:System.Windows.Forms.MaskedTextBox.Mask%2A>   
 <xref:System.Windows.Forms.MaskedTextBox></xref:System.Windows.Forms.MaskedTextBox>   
 [Validation de chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)   
 [Contrôle MaskedTextBox](http://msdn.microsoft.com/library/235d6121-027d-481d-8d59-4f6794d15d0c)
