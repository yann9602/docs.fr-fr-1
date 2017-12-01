---
title: "Comment : vérifier que des chaînes sont dans un format d'adresse de messagerie valide"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET Framework], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, e-mail strings
- input, checking
- strings [.NET Framework], examples [Visual Basic]
- e-mail [.NET Framework], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
caps.latest.revision: "30"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03623cc4086981dc321aafe3020dcd571b74d9bc
ms.sourcegitcommit: 9c4b8d457ffb8d134c9d55c6d7682a0f22e2b9a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2017
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Comment : vérifier que des chaînes sont dans un format d'adresse de messagerie valide
L'exemple suivant utilise une expression régulière pour vérifier qu'une chaîne est dans un format d'adresse de messagerie valide.  
  
## <a name="example"></a>Exemple  
 L'exemple définit une méthode `IsValidEmail` qui retourne la valeur `true` si la chaîne contient une adresse de messagerie valide et la valeur `false` dans le cas contraire, mais qui n'effectue aucune autre action.  
  
 Pour vérifier que l'adresse de messagerie est valide, la méthode `IsValidEmail` appelle la méthode <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> avec le modèle d'expression régulière `(@)(.+)$` pour séparer le nom de domaine de l'adresse de messagerie. Le troisième paramètre est un délégué <xref:System.Text.RegularExpressions.MatchEvaluator> qui représente la méthode qui traite et remplace le texte correspondant. Le modèle d'expression régulière est interprété comme suit.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`(@)`|Correspond à l'arobase (@). Il s'agit du premier groupe de capture.|  
|`(.+)`|Correspond à une ou plusieurs occurrences d'un caractère quelconque. Il s'agit du deuxième groupe de capture.|  
|`$`|Termine la correspondance à la fin de la chaîne.|  
  
 Le nom de domaine avec le caractère @ est passé à la méthode `DomainMapper` , qui utilise la classe <xref:System.Globalization.IdnMapping> pour convertir les caractères Unicode situés en dehors de la plage de caractères US-ASCII au format Punycode. La méthode affecte également à l'indicateur `invalid` la valeur `True` si la méthode <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> détecte des caractères non valides dans le nom de domaine. La méthode retourne le nom de domaine Punycode précédé du symbole @ à la méthode `IsValidEmail` .  
  
 La méthode `IsValidEmail` appelle alors la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> pour vérifier que l'adresse est conforme à un modèle d'expression régulière.  
  
 Notez que la méthode `IsValidEmail` n'effectue pas d'authentification pour valider l'adresse de messagerie. Elle détermine simplement si son format est valide pour une adresse de messagerie. En outre, la méthode `IsValidEmail` ne vérifie pas si le nom de domaine de premier niveau est un nom de domaine valide répertorié dans la [base de données des zones racines de l’IANA](https://www.iana.org/domains/root/db). Cela nécessite une opération de recherche. À la place, l'expression régulière vérifie simplement que le nom de domaine de niveau supérieur comprend entre deux et vingt-quatre caractères ASCII, les premier et dernier caractères étant des caractères alphanumériques, les autres des caractères alphanumériques ou un trait d'union (-).  
  
 [!code-csharp[RegularExpressions.Examples.Email#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#7)]
 [!code-vb[RegularExpressions.Examples.Email#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#7)]  
  
 Dans cet exemple, le modèle d'expression régulière ``^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`{}|~\w])*)(?<=[0-9a-z])@))(?([)([(\d{1,3}.){3}\d{1,3}])|(([0-9a-z][-0-9a-z]*[0-9a-z]*.)+[a-z0-9][-a-z0-9]{0,22}[a-z0-9]))$`` est interprété de la manière indiquée dans le tableau ci-dessous. Notez que l'expression régulière est compilée à l'aide de l'indicateur <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.  
  
|Modèle|Description|  
|-------------|-----------------|  
|`^`|Commence la recherche de correspondance au début de la chaîne.|  
|`(?(")`|Détermine si le premier caractère est un guillemet. `(?(")` est le début d'une construction d'alternative.|  
|`(?("")("".+?(?<!\\)""@)`|Si le premier caractère correspond à des guillemets, établit une correspondance avec des guillemets ouvrants suivis d'au moins une occurrence d'un caractère quelconque, suivie de guillemets fermants. Les guillemets doubles fermants ne doit pas être précédé par une barre oblique inverse (\\). `(?<!` est le début d'une assertion de postanalyse négative de largeur nulle. La chaîne doit se terminer par un arobase (@).|  
|`&#124;(([0-9a-z]`|Si le premier caractère n'est pas un guillemet, établit une correspondance avec un caractère alphabétique de a à z ou de A à Z (la comparaison ne respecte pas la casse) ou un chiffre (de 0 à 9).|  
|`(\.(?!\.))`|Si le caractère suivant est un point, établit une correspondance avec un point. Dans le cas contraire, effectue une préanalyse du caractère suivant et continue la recherche de correspondances. `(?!\.)` est une assertion de préanalyse négative de largeur nulle qui empêche deux points consécutifs de s'afficher dans la partie locale d'une adresse de messagerie.|  
|``&#124;[-!#\$%&'\*\+/=\?\^`{}\&#124;~\w]``|Si le caractère suivant n’est pas un point, établit une correspondance avec un caractère alphabétique quelconque ou l’un des caractères suivants : -!#$%'*+=?^`{}&#124;~.|  
|``((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^`{}\&#124;~\w])*``|Établit une correspondance avec le modèle d'alternative (un point suivi d'un autre caractère qu'un point, ou l'un des caractères) zéro, une ou plusieurs fois.|  
|`@`|Correspond à l'arobase (@).|  
|`(?<=[0-9a-z])`|Continue la recherche de correspondances si le caractère qui précède le caractère @ est compris entre A et Z, a et z, ou 0 et 9. La construction `(?<=[0-9a-z])` définit une assertion de postanalyse positive de largeur nulle.|  
|`(?(\[)`|Vérifie si le caractère qui suit @ est un crochet ouvrant.|  
|`(\[(\d{1,3}\.){3}\d{1,3}\])`|S'il s'agit d'un crochet ouvrant, établit une correspondance avec le crochet ouvrant suivi d'une adresse IP (quatre ensembles de un à trois chiffres, chaque ensemble étant séparé par un point) et d'un crochet fermant.|  
|`&#124;(([0-9a-z][-0-9a-z]*[0-9a-z]*\.)+`|Si le caractère qui suit @ n’est pas un crochet ouvrant, correspondance un caractère alphanumérique avec une valeur de A-Z, a-z ou 0-9, suivi par zéro ou plusieurs occurrences d’un trait d’union, suivi par zéro ou un caractère alphanumérique avec une valeur de A-Z, a-z ou 0-9 , suivi d’un point. Ce modèle peut être répété une ou plusieurs fois et doit être suivi du nom de domaine de niveau supérieur.|  
|`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))`|Le nom de domaine de niveau supérieur doit commencer et se terminer par un caractère alphanumérique (compris entre a et z, A et Z ou 0 et 9). Il peut également comprendre entre zéro et 22 caractères ASCII (soit des caractères alphanumériques, soit des traits d'union).|  
|`$`|Termine la correspondance à la fin de la chaîne.|  
  
> [!NOTE]
>  Au lieu d'utiliser une expression régulière pour valider une adresse de messagerie, vous pouvez recourir à la classe <xref:System.Net.Mail.MailAddress?displayProperty=nameWithType>. Pour déterminer si une adresse de messagerie est valide, transmettez l'adresse de messagerie au constructeur de classe <xref:System.Net.Mail.MailAddress.%23ctor%28System.String%29?displayProperty=nameWithType>.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Les méthodes `IsValidEmail` et `DomainMapper` peuvent être incluses dans une bibliothèque de méthodes utilitaires d'expression régulière ou peuvent être incluses en tant que méthodes d'instance ou statiques privées dans la classe d'application.  
  
 Pour les inclure dans une bibliothèque d'expressions régulières, copiez-collez le code dans un projet de bibliothèque de classes Visual Studio. Vous pouvez aussi copier-coller le code dans un fichier texte, puis le compiler depuis la ligne de commande à l'aide d'une commande semblable à celle-ci (en supposant que le nom du fichier de code source soit RegexUtilities.cs ou RegexUtilities.vb) :  
  
```csharp  
csc /t:library RegexUtilities.cs  
```  
  
```vb  
vbc /t:library RegexUtilities.vb  
```  
  
 Vous pouvez également utiliser la méthode <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> pour inclure cette expression régulière dans une bibliothèque d'expressions régulières.  
  
 Si elles sont utilisées dans une bibliothèque d'expressions régulières, vous pouvez les appeler en utilisant un code semblable au suivant :  
  
 [!code-csharp[RegularExpressions.Examples.Email#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Email/cs/example4.cs#8)]
 [!code-vb[RegularExpressions.Examples.Email#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Email/vb/example4.vb#8)]  
  
 En supposant que vous ayez créé une bibliothèque de classes nommée RegexUtilities.dll qui comprenne votre expression régulière de validation d'e-mail, vous pouvez compiler cet exemple de l'une des manières suivantes :  
  
-   Dans Visual Studio, en créant une application console et en ajoutant une référence à RegexUtilities.dll dans votre projet.  
  
-   À partir de la ligne de commande, en copiant-collant le code source dans un fichier texte, puis en le compilant avec une commande semblable à la suivante (en supposant que le nom du fichier de code source soit Example.cs ou Example.vb) :  
  
    ```csharp  
    csc Example.cs /r:RegexUtilities.dll  
    ```  
  
    ```vb  
    vbc Example.vb /r:RegexUtilities.dll  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [.NET Framework (expressions régulières)](../../../docs/standard/base-types/regular-expressions.md)
