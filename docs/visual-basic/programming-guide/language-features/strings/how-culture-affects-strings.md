---
title: "Comment les informations de culture affectent les chaînes dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- locale [Visual Basic], effect on strings
- strings [Visual Basic], locale dependence
ms.assetid: c4664444-ee0d-47bf-bef1-eaa3c54bdd7f
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b61f008edc446445fd5873b6138b64f29e0b8b8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-culture-affects-strings-in-visual-basic"></a>Comment les informations de culture affectent les chaînes dans Visual Basic
Cette page d’aide décrit comment [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] utilise les informations pour effectuer des conversions de chaînes et des comparaisons de culture.  
  
## <a name="when-to-use-culture-specific-strings"></a>Quand utiliser les chaînes spécifiques à la Culture  
 En règle générale, vous devez utiliser des chaînes spécifiques à la culture pour toutes les données présentées à lire à partir d’utilisateurs et utiliser des chaînes de la culture dite indifférente pour les données internes de votre application.  
  
 Par exemple, si votre application demande aux utilisateurs d’entrer une date sous forme de chaîne, il doit attendre les utilisateurs à mettre en forme les chaînes en fonction de leur culture et l’application doit convertir la chaîne de façon appropriée. Si votre application présente ensuite cette date dans son interface utilisateur, il doit présenter à la culture de l’utilisateur.  
  
 Toutefois, si l’application télécharge la date vers un serveur central, il doit mettre en forme la chaîne en fonction d’une culture spécifique, afin d’éviter toute confusion entre des formats de date potentiellement différents.  
  
## <a name="culture-sensitive-functions"></a>Fonctions dépendantes de la culture  
 Tous les le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] des fonctions de conversion de chaînes (à l’exception de la `Str` et `Val` fonctions) utilisent les informations de culture de l’application pour vous assurer que les conversions et les comparaisons sont appropriés pour la culture de la utilisateur de l’application.  
  
 La clé avec succès à l’aide de fonctions de conversion de chaînes dans les applications qui s’exécutent sur des ordinateurs avec des paramètres de culture différent est de comprendre les fonctions qui utilisent un paramètre de culture spécifique, et qui utilisent les paramètres de culture actuels. Notez que les paramètres de culture de l’application sont, par défaut, héritées à partir des paramètres de culture du système d’exploitation. Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Strings.Asc%2A>, <xref:Microsoft.VisualBasic.Strings.AscW%2A>, <xref:Microsoft.VisualBasic.Strings.Chr%2A>, <xref:Microsoft.VisualBasic.Strings.ChrW%2A>, <xref:Microsoft.VisualBasic.Strings.Format%2A>, <xref:Microsoft.VisualBasic.Conversion.Hex%2A>, <xref:Microsoft.VisualBasic.Conversion.Oct%2A>, et [les fonctions de Conversion de Type](../../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Le `Str` (convertit les nombres en chaînes) et `Val` les fonctions (convertit des chaînes en nombres) n’utilisent pas les informations de culture de l’application lors de la conversion entre des chaînes et des nombres. Au lieu de cela, ils reconnaissent uniquement le point (.) comme séparateur décimal valid. Les culture analogues de ces fonctions sont les suivantes :  
  
-   **Conversions qui utilisent la culture actuelle.** Le `CStr` et `Format` fonctions convertissent un nombre en une chaîne et le `CDbl` et `CInt` fonctions convertissent une chaîne en un nombre.  
  
-   **Conversions qui utilisent une culture spécifique.** Chaque objet numérique a une `ToString(IFormatProvider)` méthode qui convertit un nombre en une chaîne, et une `Parse(String, IFormatProvider)` méthode qui convertit une chaîne en un nombre. Par exemple, le `Double` type fournit le <xref:System.Double.ToString%28System.IFormatProvider%29> et <xref:System.Double.Parse%28System.String%2CSystem.IFormatProvider%29> méthodes.  
  
 Pour plus d’informations, consultez <xref:Microsoft.VisualBasic.Conversion.Str%2A> et <xref:Microsoft.VisualBasic.Conversion.Val%2A>.  
  
## <a name="using-a-specific-culture"></a>À l’aide d’une Culture spécifique  
 Imaginez que vous développez une application qui envoie une date (sous formatée de chaîne) à un service Web. Dans ce cas, votre application doit utiliser une culture spécifique pour la conversion de chaîne. Pour illustrer la raison pour laquelle, examinez le résultat de l’utilisation de la date <xref:System.DateTime.ToString> méthode : Si votre application utilise cette méthode pour mettre en forme la date du 4 juillet 2005, elle retourne « 7/4/2005 12:00:00 AM » lorsqu’il est exécuté avec la culture anglais des États-Unis (US), mais elle retourne » 04.07.2005 00:00:00 » lorsqu’il est exécuté avec la culture allemande (fr-fr).  
  
 Lorsque vous avez besoin effectuer une conversion de chaîne dans un format de culture spécifique, vous devez utiliser le `CultureInfo` classe qui est intégrée dans le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Vous pouvez créer un nouveau `CultureInfo` objet pour une culture spécifique en passant le nom de la culture à le <xref:System.Globalization.CultureInfo.%23ctor%2A> constructeur. Les noms de cultures pris en charge sont répertoriés dans le <xref:System.Globalization.CultureInfo> page d’aide de classe.  
  
 Vous pouvez également obtenir une instance de la *culture dite indifférente* à partir de la <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> propriété. La culture dite indifférente est basée sur la culture anglaise, mais il existe certaines différences. Par exemple, la culture dite indifférente spécifie une horloge de 24 heures au lieu d’une horloge au format 12 heures.  
  
 Pour convertir une date à la chaîne de culture, passez le <xref:System.Globalization.CultureInfo> objet à l’objet de date <xref:System.DateTime.ToString%28System.IFormatProvider%29> (méthode). Par exemple, le code suivant affiche « 07/04/2005 00:00:00 », indépendamment des paramètres de culture de l’application.  
  
 [!code-vb[VbVbalrConcepts#1](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/how-culture-affects-strings_1.vb)]  
  
> [!NOTE]
>  Littéraux de date sont toujours interprétées en fonction de la culture.  
  
## <a name="comparing-strings"></a>Comparaison de chaînes  
 Il existe deux situations importantes où les comparaisons de chaînes sont nécessaires :  
  
-   **Tri des données à afficher pour l’utilisateur.** Utilisez les opérations basées sur la culture actuelle afin de trier les chaînes en conséquence.  
  
-   **Déterminer si deux chaînes internes d’une application correspondent exactement (en général pour des raisons de sécurité).** Utilisez des opérations qui ignorent la culture actuelle.  
  
 Vous pouvez effectuer les deux types de comparaisons avec la [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Strings.StrComp%2A> (fonction). Spécifiez le paramètre facultatif `Compare` argument pour contrôler le type de comparaison : `Text` pour la plupart des entrées et sorties `Binary` pour déterminer les correspondances exactes.  
  
 Le `StrComp` fonction retourne un entier qui indique la relation entre les deux chaînes comparées selon l’ordre de tri. Une valeur positive pour le résultat indique que la première chaîne est supérieure à la deuxième chaîne. Un résultat négatif indique la première chaîne est plus petite et la valeur zéro indique l’égalité entre les chaînes.  
  
 [!code-vb[VbVbalrStrings#22](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_2.vb)]  
  
 Vous pouvez également utiliser le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] partenaire de la `StrComp` (fonction), la <xref:System.String.Compare%2A?displayProperty=nameWithType> (méthode). Il s’agit d’une méthode statique, la surcharge de la classe string de base. L’exemple suivant illustre l’utilisation de cette méthode :  
  
 [!code-vb[VbVbalrStrings#48](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-culture-affects-strings_3.vb)]  
  
 Pour un contrôle plus précis sur la façon dont les comparaisons sont effectuées, vous pouvez utiliser les surcharges supplémentaires de la <xref:System.String.Compare%2A> (méthode). Avec la <xref:System.String.Compare%2A?displayProperty=nameWithType> (méthode), vous pouvez utiliser la `comparisonType` argument afin de spécifier le type de comparaison à utiliser.  
  
|La valeur pour `comparisonType` argument|Type de comparaison|Quand l'utiliser|  
|---|---|---|  
|`Ordinal`|Comparaison en fonction des octets de composant de chaînes.|Utilisez cette valeur lors de la comparaison : identificateurs respectant la casse, les paramètres de sécurité ou autres identificateurs non linguistiques où les octets doivent correspondre exactement.|  
|`OrdinalIgnoreCase`|Comparaison en fonction des octets de composant de chaînes.<br /><br /> `OrdinalIgnoreCase`utilise les informations de culture dite indifférente pour déterminer quand les deux caractères diffèrent uniquement par la casse.|Utilisez cette valeur lors de la comparaison : identificateurs de non-respect de la casse, les paramètres de sécurité et les données stockées dans Windows.|  
|`CurrentCulture` ou `CurrentCultureIgnoreCase`|Comparaison en fonction de l’interprétation des chaînes dans la culture actuelle.|Utilisez ces valeurs lors de la comparaison : données qui sont affichées à l’utilisateur, la plupart des entrées d’utilisateur et autres données qui nécessitent une interprétation linguistique.|  
|`InvariantCulture` ou `InvariantCultureIgnoreCase`|Comparaison en fonction de l’interprétation des chaînes dans la culture dite indifférente.<br /><br /> Cela est différent de celui du `Ordinal` et `OrdinalIgnoreCase`, car la culture dite indifférente traite les caractères en dehors de sa plage admise comme des caractères invariantes équivalents.|Utilisez ces valeurs uniquement lors de la comparaison des données persistantes ou l’affichage des données linguistiquement pertinentes qui requiert un ordre de tri fixe.|  
  
### <a name="security-considerations"></a>Considérations relatives à la sécurité  
 Si votre application prend des décisions de sécurité en fonction du résultat d’une comparaison ou d’une opération de changement de casse, l’opération doit utiliser la <xref:System.String.Compare%2A?displayProperty=nameWithType> (méthode), puis transmettez `Ordinal` ou `OrdinalIgnoreCase` pour la `comparisonType` argument.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Globalization.CultureInfo>  
 [Introduction aux chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [Fonctions de conversion de types](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
