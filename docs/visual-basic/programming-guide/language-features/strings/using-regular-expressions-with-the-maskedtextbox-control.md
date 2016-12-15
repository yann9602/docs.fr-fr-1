---
title: "Using Regular Expressions with the MaskedTextBox Control in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "strings [Visual Basic], regular expressions"
  - "strings [Visual Basic], masked edit"
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Using Regular Expressions with the MaskedTextBox Control in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cet exemple montre comment convertir des expressions régulières simples pour utiliser le contrôle <xref:System.Windows.Forms.MaskedTextBox>.  
  
## Description du langage de masquage  
 Le langage de masquage <xref:System.Windows.Forms.MaskedTextBox> standard est basé sur celui utilisé par le contrôle `Masked Edit` dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0 et doit être connu des utilisateurs qui migrent depuis cette plateforme.  
  
 La propriété <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> du contrôle <xref:System.Windows.Forms.MaskedTextBox> spécifie le masque de saisie à utiliser.  Ce masque doit être une chaîne composée d'un ou de plusieurs des éléments de masquage répertoriés dans le tableau suivant.  
  
|Élément de masquage|Description|Élément d'expression régulière|  
|-------------------------|-----------------|------------------------------------|  
|0|Chiffre unique entre 0 et 9.  Entrée obligatoire.|\\d|  
|9|Chiffre ou espace.  Entrée facultative.|\[ \\d\]?|  
|\#|Chiffre ou espace.  Entrée facultative.  Si cette position reste vide dans le masque, elle est restituée sous la forme d'un espace.  Les signes plus \(\+\) et moins \(\-\) sont autorisés.|\[ \\d\+\-\]?|  
|L|Lettre ASCII.  Entrée obligatoire.|\[a\-zA\-Z\]|  
|?|Lettre ASCII.  Entrée facultative.|\[a\-zA\-Z\]?|  
|&|Character  Entrée obligatoire.|\[\\p{Ll}\\p{Lu}\\p{Lt}\\p{Lm}\\p{Lo}\]|  
|C|Character  Entrée facultative.|\[\\p{Ll}\\p{Lu}\\p{Lt}\\p{Lm}\\p{Lo}\]?|  
|A|Chiffre alphanumérique.  Entrée facultative.|\\W|  
|.|Espace réservé à la décimale approprié à la culture.|Non disponible.|  
|,|Espace réservé aux milliers approprié à la culture.|Non disponible.|  
|:|Séparateur d'heure approprié à la culture.|Non disponible.|  
|\/|Séparateur de date approprié à la culture.|Non disponible.|  
|$|Symbole monétaire approprié à la culture.|Non disponible.|  
|\<|Convertit tous les caractères suivants en minuscules.|Non disponible.|  
|\>|Convertit tous les caractères suivants en majuscules.|Non disponible.|  
|&#124;|Annule un décalage vers le haut ou vers le bas effectué précédemment.|Non disponible.|  
|\\|Remplace un caractère de masque par un littéral. "  \\\\" est la séquence d'échappement pour une barre oblique inverse.|\\|  
|Tous les autres caractères.|Littéraux.  Tous les éléments qui ne sont pas de masque apparaissent tels quels dans <xref:System.Windows.Forms.MaskedTextBox>.|Tous les autres caractères.|  
  
 Les symboles de la décimale \(.\), des millièmes \(\), de l'heure \(:\), de la date \(\/\) et de la monnaie \($\) affichent par défaut les symboles tels que définis par la culture de l'application.  Vous pouvez les forcer à afficher les symboles d'une autre culture à l'aide de la propriété <xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>.  
  
## Expressions régulières et masques  
 Bien que vous puissiez utiliser des expressions régulières et des masques pour valider les entrées d'utilisateur, ils ne sont pas tout à fait équivalents.  Les expressions régulières peuvent exprimer des modèles plus complexes que les masques, mais les masques peuvent exprimer les mêmes informations plus succinctement et dans un format culturellement pertinent.  
  
 Le tableau suivant compare quatre expressions régulières et le masque équivalent pour chacune d'elles.  
  
|Expression régulière|Masque|Remarques|  
|--------------------------|------------|---------------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|Le caractère `/` dans le masque est un séparateur de date logique, et est présenté à l'utilisateur sous la forme du séparateur de date approprié à la culture actuelle de l'application.|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|Date \(jour, abréviation du mois et année\) au format américain dans lequel l'abréviation à trois lettres du mois est affichée avec une lettre majuscule initiale suivie de deux lettres minuscules.|  
|`(\(\d{3}\)-)?  \d{3}-d{4}`|`(999)-000-0000`|Numéro de téléphone aux États\-Unis, indicatif régional facultatif.  Si l'utilisateur ne souhaite pas entrer les caractères facultatifs, il peut entrer des espaces ou placer le pointeur de la souris directement  à la position représentée par le premier 0 dans le masque.|  
|`$\d{6}.00`|`$999,999.00`|Valeur monétaire comprise entre 0 et 999999.  Les caractères de la monnaie, des millièmes et de la décimale sont remplacés au moment de l'exécution par leurs équivalents spécifiques à la culture.|  
  
## Voir aussi  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>   
 <xref:System.Windows.Forms.MaskedTextBox>   
 [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)   
 [MaskedTextBox, contrôle](../Topic/MaskedTextBox%20Control%20\(Windows%20Forms\).md)