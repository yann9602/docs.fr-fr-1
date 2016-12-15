---
title: "How Culture Affects Strings in Visual Basic | Microsoft Docs"
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
  - "locale, effect on strings"
  - "strings [Visual Basic], locale dependence"
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How Culture Affects Strings in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette page d'aide décrit comment [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] utilise les informations de culture pour effectuer des conversions et des comparaisons de chaînes.  
  
## Période à laquelle utiliser les chaînes spécifiques à la culture  
 En général, vous devez utiliser des chaînes spécifiques à la culture pour toutes les données présentées aux utilisateurs et lues par ces derniers, et utiliser des chaînes de culture dites indifférentes pour les données internes de votre application.  
  
 Par exemple, si votre application demande aux utilisateurs d'entrer une date en tant que chaîne, elle doit s'attendre à ce que les utilisateurs mettent en forme les chaînes en fonction de leur culture et l'application doit convertir la chaîne en conséquence.  Si votre application présente ensuite la date dans son interface utilisateur, elle doit le faire dans la culture de l'utilisateur.  
  
 Toutefois, si l'application télécharge la date vers un serveur central, elle doit mettre en forme la chaîne en fonction d'une culture spécifique pour éviter la confusion entre des formats de date potentiellement différents.  
  
## Fonctions dépendantes de la culture  
 Toutes les fonctions de conversion de chaînes [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] \(à l'exception des fonctions `Str` et `Val`\) utilisent les informations de culture de l'application pour vérifier que les conversions et les comparaisons sont conformes à la culture de l'utilisateur de l'application.  
  
 Pour utiliser avec succès les fonctions de conversion de chaînes dans les applications qui s'exécutent sur les ordinateurs ayant des paramètres de culture différents, vous devez connaître les fonctions qui utilisent un paramètre de culture spécifique et celles qui utilisent le paramètre de culture actuel.  Notez que les paramètres de culture de l'application sont, par défaut, hérités des paramètres de culture du système d'exploitation.  Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A> et [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Les fonctions `Str` \(convertit des nombres en chaînes\) et `Val` \(convertit des chaînes en nombres\) n'utilisent pas les informations de culture de l'application lors de la conversion entre les chaînes et les nombres.  Elles ne reconnaissent en fait que le point \(.\) comme séparateur décimal valide.  Les analogues de ces fonctions sensibles à l'environnement culturel sont les suivants :  
  
-   **conversions qui utilisent la culture actuelle.** Les fonctions `CStr` et `Format` convertissent un nombre en une chaîne et les fonctions `CDbl` et `CInt` convertissent une chaîne en un nombre ;  
  
-   **conversions qui utilisent une culture spécifique.** Chaque objet numérique a une méthode `ToString(IFormatProvider)` qui convertit un nombre en une chaîne, et une méthode `Parse(String, IFormatProvider)` qui convertit une chaîne en un nombre.  Par exemple, le type `Double` fournit les méthodes <xref:System.Double.ToString%28System.IFormatProvider%29> et <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29>.  
  
 Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Conversion.Str%2A> et <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## Utilisation d'une culture spécifique  
 Supposons que vous développez une application qui envoie une date \(mise en forme comme une chaîne\) à un service Web.  Dans ce cas, votre application doit utiliser une culture spécifique pour la conversion de la chaîne.  Pour en connaître la raison, prenez le résultat de l'utilisation de la méthode <xref:System.DateTime.ToString> de la date : si votre application utilise cette méthode pour mettre en forme la date du 4 juillet 2005, elle retourne « 7\/4\/2005 12:00:00 AM »" lorsqu'elle est exécutée avec la culture Anglais \(États\-Unis\) \(en\-US\), mais elle retourne « 04.07.2005 00:00:00 » lorsqu'elle est exécutée avec la culture Allemand \(de\-DE\).  
  
 Lorsque vous devez exécuter la conversion d'une chaîne en un format de culture spécifique, vous devez utiliser la classe `CultureInfo` qui est intégrée dans le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].  Vous pouvez créer un objet `CultureInfo` pour une culture spécifique en passant le nom de la culture au constructeur <xref:System.Globalization.CultureInfo.%23ctor%2A>.  Les noms de cultures pris en charge sont répertoriés dans la page d'aide de la classe <xref:System.Globalization.CultureInfo>.  
  
 Vous pouvez également obtenir une instance de la *culture dite indifférente* à partir de la propriété <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.  La culture dite indifférente est basée sur la culture anglaise, mais il existe certaines différences.  Par exemple, elle spécifie une horloge de 24 heures au lieu d'une horloge de 12 heures.  
  
 Pour remplacer une date par la chaîne de culture, passez l'objet <xref:System.Globalization.CultureInfo> à la méthode <xref:System.DateTime.ToString%28System.IFormatProvider%29> de l'objet de la date.  Par exemple, le code suivant affiche « 07\/04\/2005 00:00:00 », quels que soient les paramètres de culture de l'application.  
  
 [!code-vb[VbVbalrConcepts#1](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/how-culture-affects-strings_1.vb)]  
  
> [!NOTE]
>  Les littéraux de date sont toujours interprétés en fonction de la culture anglophone.  
  
## Comparaison de chaînes  
 Il existe deux situations importantes dans lesquelles les comparaisons de chaînes sont nécessaires :  
  
-   **triage des données à afficher pour l'utilisateur.** Utilisez les opérations en fonction de la culture actuelle afin que les chaînes puissent être triées correctement ;  
  
-   **détermination de la correspondance exacte ou non entre deux chaînes internes d'une application \(généralement pour des raisons de sécurité\).** Utilisez des opérations qui ignorent la culture actuelle.  
  
 Vous pouvez effectuer les deux types de comparaisons avec la fonction [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Strings.StrComp%2A>.  Spécifiez l'argument facultatif `Compare` pour contrôler le type de comparaison : `Text` pour la plupart des entrées et sorties, `Binary` pour déterminer les correspondances exactes.  
  
 La fonction `StrComp` retourne un entier qui indique la relation entre les deux chaînes comparées selon l'ordre de tri.  Une valeur positive du résultat indique que la première chaîne est plus grande que la seconde.  Un résultat négatif indique que la première chaîne est plus petite, tandis que la valeur zéro indique une égalité entre les chaînes.  
  
 [!code-vb[VbVbalrStrings#22](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_2.vb)]  
  
 Vous pouvez également utiliser le partenaire du [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] de la fonction `StrComp`, la méthode <xref:System.String.Compare%2A?displayProperty=fullName>.  C'est une méthode statique et surchargée de la classe String de base.  L'exemple suivant illustre l'utilisation de cette méthode :  
  
 [!code-vb[VbVbalrStrings#48](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_3.vb)]  
  
 Pour un contrôle plus fin de la manière dont les comparaisons sont effectuées, vous pouvez utiliser des surcharges supplémentaires de la méthode <xref:System.String.Compare%2A>.  Avec la méthode <xref:System.String.Compare%2A?displayProperty=fullName>, vous pouvez utiliser l'argument `comparisonType` pour spécifier le type de comparaison à utiliser.  
  
||||  
|-|-|-|  
|Valeur de l'argument `comparisonType`|Type de comparaison|Quand l'utiliser|  
|`Ordinal`|Comparaison en fonction des octets de composant des chaînes.|Utilisez cette valeur lors de la comparaison des identificateurs respectant les majuscules et les minuscules, des paramètres relatifs à la sécurité ou des autres identificateurs non linguistiques où les octets doivent correspondre exactement.|  
|`OrdinalIgnoreCase`|Comparaison en fonction des octets de composant des chaînes.<br /><br /> `OrdinalIgnoreCase` utilise les informations de culture dite indifférente pour déterminer à quel moment deux caractères ne diffèrent que dans la mise en majuscules.|Utilisez cette valeur lors de la comparaison des identificateurs ne respectant pas les majuscules et les minuscules, des paramètres relatifs à la sécurité et des données stockées dans Windows.|  
|`CurrentCulture` ou `CurrentCultureIgnoreCase`|Comparaison en fonction de l'interprétation des chaînes dans la culture actuelle.|Utilisez ces valeurs lors de la comparaison des données affichées pour l'utilisateur, de la plupart des entrées d'utilisateur et des autres données qui nécessitent une interprétation linguistique.|  
|`InvariantCulture` ou `InvariantCultureIgnoreCase`|Comparaison en fonction de l'interprétation des chaînes dans la culture dite indifférente.<br /><br /> Elle est différente de `Ordinal` et de `OrdinalIgnoreCase` parce que la culture dite indifférente traite les caractères en dehors de sa plage admise comme des caractères indifférents équivalents.|Utilisez ces valeurs uniquement lors de la comparaison de la persistance des données ou de l'affichage des données linguistiquement appropriées nécessitant un ordre de tri fixe.|  
  
### Considérations sur la sécurité  
 Si votre application prend des décisions relatives à la sécurité en fonction du résultat d'une comparaison ou d'une opération de modification des majuscules et des minuscules, l'opération doit utiliser la méthode <xref:System.String.Compare%2A?displayProperty=fullName> et passer `Ordinal` ou `OrdinalIgnoreCase` pour l'argument `comparisonType`.  
  
## Voir aussi  
 <xref:System.Globalization.CultureInfo>   
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)