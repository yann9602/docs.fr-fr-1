---
title: "La Culture affectent les chaînes en Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- locale, effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 63228a40897b29d0324be73ca1a17bcb19af2a16
ms.lasthandoff: 03/13/2017

---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Comment les informations de culture affectent les chaînes dans Visual Basic
Cette page d’aide décrit comment [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] utilise les informations pour effectuer des conversions de chaînes et des comparaisons de culture.  
  
## <a name="when-to-use-culture-specific-strings"></a>Quand utiliser des chaînes spécifiques à la Culture  
 En règle générale, vous devez utiliser des chaînes spécifiques à la culture pour toutes les données présentées à et lire à partir d’utilisateurs et utiliser des chaînes de la culture dite indifférente pour les données internes de votre application.  
  
 Par exemple, si votre application demande aux utilisateurs d’entrer une date sous forme de chaîne, il doit attendre les utilisateurs à mettre en forme les chaînes en fonction de leur culture et l’application doit convertir la chaîne en conséquence. Si votre application présente ensuite cette date dans son interface utilisateur, elle doit le présenter dans la culture de l’utilisateur.  
  
 Toutefois, si l’application télécharge la date vers un serveur central, il doit mettre en forme la chaîne en fonction d’une culture spécifique, afin d’éviter toute confusion entre des formats de date potentiellement différents.  
  
## <a name="culture-sensitive-functions"></a>Fonctions dépendantes de la culture  
 Tous les [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] des fonctions de conversion de chaînes (à l’exception de la `Str` et `Val` fonctions) utilisent les informations de culture de l’application pour vous assurer que les conversions et les comparaisons sont appropriés pour la culture de l’utilisateur.  
  
 La clé à l’aide de fonctions de conversion de chaînes dans les applications qui s’exécutent sur des ordinateurs avec des paramètres de culture différentes est de comprendre les fonctions qui utilisent un paramètre de culture spécifique, et qui utilisent les paramètres de culture actuels. Notez que les paramètres de culture de l’application sont, par défaut, héritées dans les paramètres de culture du système d’exploitation. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>, et [les fonctions de Conversion de Type](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).</xref:Microsoft.VisualBasic.Conversion.Oct%2A> </xref:Microsoft.VisualBasic.Conversion.Hex%2A> </xref:Microsoft.VisualBasic.Strings.Format%2A> </xref:Microsoft.VisualBasic.Strings.ChrW%2A> </xref:Microsoft.VisualBasic.Strings.Chr%2A> </xref:Microsoft.VisualBasic.Strings.AscW%2A> </xref:Microsoft.VisualBasic.Strings.Asc%2A>  
  
 Le `Str` (convertit des nombres en chaînes) et `Val` fonctions de (convertit des chaînes en nombres) n’utilisent pas les informations de culture de l’application lors de la conversion entre des chaînes et des nombres. Au lieu de cela, ils ne reconnaissent que le point (.) comme séparateur décimal valid. Les culture analogues de ces fonctions sont les suivantes :  
  
-   **Conversions qui utilisent la culture actuelle.** Le `CStr` et `Format` fonctions convertissent un nombre en une chaîne et le `CDbl` et `CInt` fonctions convertissent une chaîne en un nombre.  
  
-   **Conversions qui utilisent une culture spécifique.** Chaque objet numérique a une `ToString(IFormatProvider)` méthode qui convertit un nombre en une chaîne, et une `Parse(String, IFormatProvider)` méthode qui convertit une chaîne en un nombre. Par exemple, le `Double` type fournit le <xref:System.Double.ToString%28System.IFormatProvider%29>et <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29>méthodes.</xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> </xref:System.Double.ToString%28System.IFormatProvider%29>  
  
 Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Conversion.Str%2A>et <xref:Microsoft.VisualBasic.Conversion.Val%2A>.</xref:Microsoft.VisualBasic.Conversion.Val%2A> </xref:Microsoft.VisualBasic.Conversion.Str%2A>  
  
## <a name="using-a-specific-culture"></a>À l’aide d’une Culture spécifique  
 Imaginez que vous développez une application qui envoie une date (sous formatée de chaîne) à un service Web. Dans ce cas, votre application doit utiliser une culture spécifique pour la conversion de chaîne. Pour illustrer pourquoi, examinez le résultat de l’utilisation de la date <xref:System.DateTime.ToString>(méthode) : Si votre application utilise cette méthode pour mettre en forme la date du 4 juillet 2005, elle retourne « 7/4/2005 12:00:00 AM » lorsqu’il est exécuté avec la culture anglais (États-Unis) (en-US), mais elle retourne « 04.07.2005 00:00:00 » lorsqu’il est exécuté avec la culture Allemand (de-DE).</xref:System.DateTime.ToString>  
  
 Lorsque vous avez besoin effectuer une conversion de chaîne dans un format de culture spécifique, vous devez utiliser le `CultureInfo` classe qui est intégrée dans le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]. Vous pouvez créer un nouveau `CultureInfo` objet pour une culture spécifique en passant le nom de la culture à le <xref:System.Globalization.CultureInfo.%23ctor%2A>constructeur.</xref:System.Globalization.CultureInfo.%23ctor%2A> Les noms de culture prise en charge sont répertoriés dans le <xref:System.Globalization.CultureInfo>page d’aide classe.</xref:System.Globalization.CultureInfo>  
  
 Vous pouvez également obtenir une instance de la *culture dite indifférente* à partir de la <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>propriété.</xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> La culture dite indifférente est basée sur la culture anglaise, mais il existe certaines différences. Par exemple, la culture dite indifférente spécifie une horloge de 24 heures au lieu d’une horloge de 12 heures.  
  
 Pour convertir une date à la chaîne de culture, passez le <xref:System.Globalization.CultureInfo>objet à l’objet de date <xref:System.DateTime.ToString%28System.IFormatProvider%29>méthode.</xref:System.DateTime.ToString%28System.IFormatProvider%29> </xref:System.Globalization.CultureInfo> Par exemple, le code suivant affiche « 07/04/2005 00:00:00 », indépendamment des paramètres de culture de l’application.  
  
 [!code-vb[VbVbalrConcepts n °&1;](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/how-culture-affects-strings_1.vb)]  
  
> [!NOTE]
>  Littéraux de date sont toujours interprétées en fonction de la culture.  
  
## <a name="comparing-strings"></a>Comparaison de chaînes  
 Il existe deux situations importantes où les comparaisons de chaînes sont nécessaires :  
  
-   **Tri des données pour l’affichage à l’utilisateur.** Utiliser des opérations en fonction de la culture actuelle afin de trier les chaînes en conséquence.  
  
-   **Déterminer si deux chaînes internes d’une application correspondent exactement (généralement pour des raisons de sécurité).** Utilisez des opérations qui ignorent la culture actuelle.  
  
 Vous pouvez effectuer les deux types de comparaisons avec la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Strings.StrComp%2A>fonction.</xref:Microsoft.VisualBasic.Strings.StrComp%2A> Spécifiez le paramètre facultatif `Compare` argument pour contrôler le type de comparaison : `Text` pour la plupart des entrées et sorties `Binary` pour déterminer les correspondances exactes.  
  
 Le `StrComp` fonction retourne un entier qui indique la relation entre les deux chaînes comparées selon l’ordre de tri. Une valeur positive pour le résultat indique que la première chaîne est supérieure à la deuxième chaîne. Un résultat négatif indique la première chaîne est plus petite et zéro indique une égalité entre les chaînes.  
  
 [!code-vb[VbVbalrStrings&#22;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_2.vb)]  
  
 Vous pouvez également utiliser le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] partenaire de la `StrComp` (fonction), la <xref:System.String.Compare%2A?displayProperty=fullName>méthode.</xref:System.String.Compare%2A?displayProperty=fullName> Il s’agit d’une méthode statique et surchargée de la classe string de base. L’exemple suivant illustre l’utilisation de cette méthode :  
  
 [!code-vb[VbVbalrStrings&#48;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_3.vb)]  
  
 Pour un contrôle plus précis sur la manière dont les comparaisons sont effectuées, vous pouvez utiliser des surcharges supplémentaires de la <xref:System.String.Compare%2A>méthode.</xref:System.String.Compare%2A> Avec la <xref:System.String.Compare%2A?displayProperty=fullName>(méthode), vous pouvez utiliser la `comparisonType` argument pour spécifier le type de comparaison à utiliser.</xref:System.String.Compare%2A?displayProperty=fullName>  
  
|La valeur pour `comparisonType` argument|Type de comparaison|Quand l'utiliser|  
|---|---|---|  
|`Ordinal`|Comparaison en fonction des octets de composant des chaînes.|Utilisez cette valeur lors de la comparaison : identificateurs respectant la casse, les paramètres de sécurité ou d’autres identificateurs non linguistiques où les octets doivent correspondre exactement.|  
|`OrdinalIgnoreCase`|Comparaison en fonction des octets de composant des chaînes.<br /><br /> `OrdinalIgnoreCase`utilise les informations de culture dite indifférente pour déterminer quand les deux caractères diffèrent uniquement par la casse.|Utilisez cette valeur lors de la comparaison : identificateurs pas la casse, les paramètres de sécurité et les données stockées dans Windows.|  
|`CurrentCulture` ou `CurrentCultureIgnoreCase`|Comparaison basée sur l’interprétation des chaînes dans la culture actuelle.|Utilisez ces valeurs lors de la comparaison : données qui sont affichées à l’utilisateur, la plupart des entrées d’utilisateur et autres données qui nécessitent une interprétation linguistique.|  
|`InvariantCulture` ou `InvariantCultureIgnoreCase`|Comparaison basée sur l’interprétation des chaînes dans la culture dite indifférente.<br /><br /> Cela est différent de celui du `Ordinal` et `OrdinalIgnoreCase`, parce que la culture dite indifférente traite les caractères en dehors de sa plage admise comme des caractères invariants équivalents.|Utilisez ces valeurs uniquement lors de la comparaison des données persistantes ou affichage des données linguistiquement pertinentes qui requiert un ordre de tri fixe.|  
  
### <a name="security-considerations"></a>Considérations relatives à la sécurité  
 Si votre application prend des décisions de sécurité en fonction du résultat d’une comparaison ou d’une opération de changement de casse, l’opération doit utiliser le <xref:System.String.Compare%2A?displayProperty=fullName>(méthode), puis transmettez `Ordinal` ou `OrdinalIgnoreCase` pour la `comparisonType` argument.</xref:System.String.Compare%2A?displayProperty=fullName>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Globalization.CultureInfo></xref:System.Globalization.CultureInfo>   
 [Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [Fonctions de conversion de types](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
