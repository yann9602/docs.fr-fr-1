---
title: "Fonctions de cha&#238;ne (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "fonctions de string"
ms.assetid: f1bf9ac2-cbcf-4298-ae51-53182076bdc8
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Fonctions de cha&#238;ne (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Le tableau suivant répertorie les fonctions fournies par Visual Basic pour rechercher et manipuler des chaînes.  
  
|Méthode .NET Framework|Description|  
|----------------------------|-----------------|  
|<xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>|Retourne une valeur de type `Integer` qui représente le code de caractère correspondant à un caractère.|  
|<xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>|Retourne le caractère associé au code de caractère spécifié.|  
|<xref:Microsoft.VisualBasic.Strings.Filter%2A>|Retourne un tableau de base zéro et contenant un sous\-ensemble d'un tableau de chaînes \(`String`\) basé sur des critères de filtre spécifiés.|  
|<xref:Microsoft.VisualBasic.Strings.Format%2A>|Retourne une chaîne mise en forme conformément aux instructions contenues dans une expression `String` de format.|  
|<xref:Microsoft.VisualBasic.Strings.FormatCurrency%2A>|Retourne une expression sous forme de valeur monétaire utilisant le symbole monétaire défini dans le Panneau de configuration du système.|  
|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>|Retourne une expression de chaîne représentant une valeur de date\/d'heure.|  
|<xref:Microsoft.VisualBasic.Strings.FormatNumber%2A>|Retourne une expression sous forme de nombre.|  
|<xref:Microsoft.VisualBasic.Strings.FormatPercent%2A>|Retourne une expression formatée sous forme de pourcentage \(c'est\-à\-dire multipliée par 100\) avec un caractère de fin %.|  
|<xref:Microsoft.VisualBasic.Strings.InStr%2A>|Retourne un entier spécifiant la position de début de la première occurrence d'une chaîne à l'intérieur d'une autre.|  
|<xref:Microsoft.VisualBasic.Strings.InStrRev%2A>|Retourne la position de la première occurrence d'une chaîne dans une autre, à partir du côté droit de la chaîne.|  
|<xref:Microsoft.VisualBasic.Strings.Join%2A>|Retourne une chaîne créée par la jonction de plusieurs sous\-chaînes contenues dans un tableau.|  
|<xref:Microsoft.VisualBasic.Strings.LCase%2A>|Retourne une chaîne ou un caractère converti en lettres minuscules.|  
|<xref:Microsoft.VisualBasic.Strings.Left%2A>|Retourne une chaîne contenant un nombre spécifié de caractères en partant de la gauche d'une chaîne.|  
|<xref:Microsoft.VisualBasic.Strings.Len%2A>|Retourne un entier contenant le nombre de caractères dans une chaîne.|  
|<xref:Microsoft.VisualBasic.Strings.LSet%2A>|Retourne une chaîne alignée à gauche contenant la chaîne spécifiée ajustée à la longueur spécifiée.|  
|<xref:Microsoft.VisualBasic.Strings.LTrim%2A>|Retourne une chaîne contenant une copie d'une chaîne spécifiée sans espaces à gauche.|  
|<xref:Microsoft.VisualBasic.Strings.Mid%2A>|Retourne une chaîne contenant un nombre spécifié de caractères d'une chaîne.|  
|<xref:Microsoft.VisualBasic.Strings.Replace%2A>|Retourne une chaîne dans laquelle une sous\-chaîne spécifiée a été remplacée par une autre sous\-chaîne, un nombre de fois déterminé.|  
|<xref:Microsoft.VisualBasic.Strings.Right%2A>|Retourne une chaîne contenant un nombre spécifié de caractères depuis la partie droite d'une chaîne.|  
|<xref:Microsoft.VisualBasic.Strings.RSet%2A>|Retourne une chaîne alignée à droite contenant la chaîne spécifiée ajustée à la longueur spécifiée.|  
|<xref:Microsoft.VisualBasic.Strings.RTrim%2A>|Retourne une chaîne contenant une copie d'une chaîne spécifiée sans espaces à droite.|  
|<xref:Microsoft.VisualBasic.Strings.Space%2A>|Retourne une chaîne composée d'un nombre spécifié d'espaces.|  
|<xref:Microsoft.VisualBasic.Strings.Split%2A>|Retourne un tableau à une dimension de base zéro et contenant le nombre spécifié de sous\-chaînes.|  
|<xref:Microsoft.VisualBasic.Strings.StrComp%2A>|Retourne \-1, 0 ou 1, à partir du résultat d'une comparaison de chaînes.|  
|<xref:Microsoft.VisualBasic.Strings.StrConv%2A>|Retourne une chaîne convertie comme spécifié.|  
|<xref:Microsoft.VisualBasic.Strings.StrDup%2A>|Retourne une chaîne ou un objet constitué du caractère spécifié répété le nombre de fois spécifié.|  
|<xref:Microsoft.VisualBasic.Strings.StrReverse%2A>|Retourne une chaîne dans laquelle l'ordre des caractères d'une chaîne donnée a été inversé.|  
|<xref:Microsoft.VisualBasic.Strings.Trim%2A>|Retourne une chaîne contenant une copie d'une chaîne spécifiée sans espaces à gauche ni à droite.|  
|<xref:Microsoft.VisualBasic.Strings.UCase%2A>|Retourne une chaîne ou un caractère contenant la chaîne spécifiée convertie en majuscules.|  
  
 Vous pouvez utiliser l'instruction [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) pour définir si les chaînes sont comparées selon un ordre de tri de texte non sensible à la casse déterminé par les paramètres régionaux de votre système \(`Text`\) ou par les représentations binaires internes des caractères \(`Binary`\).  La méthode de comparaison de texte par défaut est `Binary`.  
  
## Exemple  
 L'exemple suivant utilise la fonction `UCase` pour retourner une version en majuscules d'une chaîne.  
  
 [!code-vb[VbVbalrStrings#31](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_1.vb)]  
  
## Exemple  
 Cet exemple utilise la fonction `LTrim` pour supprimer les espaces à gauche et la fonction `RTrim` pour supprimer les espaces à droite d'une variable chaîne.  Il utilise la fonction `Trim` pour supprimer les deux types d'espaces.  
  
 [!code-vb[VbVbalrStrings#25](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_2.vb)]  
  
## Exemple  
 L'exemple suivant utilise la fonction `Mid` pour retourner un nombre spécifié de caractères à partir d'une chaîne.  
  
 [!code-vb[VbVbalrStrings#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_3.vb)]  
  
## Exemple  
 L'exemple suivant utilise la fonction `Len` pour retourner le nombre de caractères d'une chaîne.  
  
 [!code-vb[VbVbalrStrings#33](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_4.vb)]  
  
## Exemple  
 L'exemple suivant utilise la fonction `InStr` pour retourner la position de la première occurrence d'une chaîne à l'intérieur d'une autre.  
  
 [!code-vb[VbVbalrStrings#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_5.vb)]  
  
## Exemple  
 L'exemple suivant illustre différentes utilisations de la fonction `Format` pour mettre en forme des valeurs utilisant à la fois les formats `String` et les formats définis par l'utilisateur.  Pour le séparateur de date \(`/`\), le séparateur d'heure \(`:`\) et les indicateurs AM\/PM \(`t` et `tt`\), le résultat réel mis en forme affiché par votre système dépend des paramètres régionaux utilisés par le code.  Lorsque les heures et les dates sont affichées dans l'environnement de développement, les formats d'heure abrégée et de date courte des paramètres régionaux de code sont utilisés.  
  
> [!NOTE]
>  Pour paramètres régionaux configurés avec une horloge au format 24 heures, les indicateurs AM\/PM \(`t` et `tt`\) n'affichent rien.  
  
 [!code-vb[VbVbalrStrings#27](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-functions_6.vb)]  
  
## Voir aussi  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)   
 [Visual Basic Runtime Library Members](../../../visual-basic/language-reference/runtime-library-members.md)   
 [String Manipulation Summary](../../../visual-basic/language-reference/keywords/string-manipulation-summary.md)