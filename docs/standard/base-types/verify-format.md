---
title: "Guide pratique : vérifier que des chaînes sont dans un format d’adresse e-mail valide"
description: "Guide pratique pour vérifier que des chaînes sont dans un format d’adresse e-mail valide"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6d735520-4059-4754-b34c-d117299d36f1
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 077a09152ac23c986a751f42c893e1dcca858291
ms.lasthandoff: 03/02/2017

---

# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a>Guide pratique : vérifier que des chaînes sont dans un format d’adresse e-mail valide

L'exemple suivant utilise une expression régulière pour vérifier qu'une chaîne est dans un format d'adresse e-mail valide.

## <a name="example"></a>Exemple

L'exemple définit une méthode `IsValidEmail` qui retourne la valeur `true` si la chaîne contient une adresse e-mail valide et la valeur `false` dans le cas contraire, mais qui n'effectue aucune autre action. 

Pour vérifier que l’adresse e-mail est valide, la méthode `IsValidEmail` appelle la méthode [Regex.Replace(String, String, MatchEvaluator)](xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.Text.RegularExpressions.MatchEvaluator)) avec le modèle d’expression régulière `(@)(.+)$` pour séparer le nom de domaine de l’adresse e-mail. Le troisième paramètre est un délégué [MatchEvaluator](xref:System.Text.RegularExpressions.MatchEvaluator) qui représente la méthode qui traite et remplace le texte correspondant. Le modèle d’expression régulière est interprété comme suit. 

Modèle | Description
------- | ----------- 
`(@)` | Correspond à l'arobase (@). Il s'agit du premier groupe de capture.
`(.+)` | Correspond à une ou plusieurs occurrences d'un caractère quelconque. Il s'agit du deuxième groupe de capture.
`$` | Termine la correspondance à la fin de la chaîne.
 
Le nom de domaine avec le caractère @ est passé à la méthode `DomainMapper`, qui utilise la classe [IdnMapping](xref:System.Globalization.IdnMapping) pour convertir les caractères Unicode situés en dehors de la plage de caractères US-ASCII au format Punycode. La méthode affecte également à l’indicateur `invalid` la valeur `true` si la méthode [IdnMapping.GetAscii](xref:System.Globalization.IdnMapping.GetAscii(System.String)) détecte des caractères non valides dans le nom de domaine. La méthode retourne le nom de domaine Punycode précédé du symbole @ à la méthode `IsValidEmail`. 

La méthode `IsValidEmail` appelle alors la méthode [Regex.IsMatch(String, String)](xref:System.Text.RegularExpressions.Regex.IsMatch(System.String,System.String)) pour vérifier que l’adresse est conforme à un modèle d’expression régulière. 

Notez que la méthode `IsValidEmail` n'effectue pas d'authentification pour valider l'adresse e-mail. Elle détermine simplement si son format est valide pour une adresse e-mail. En outre, la méthode `IsValidEmail` ne vérifie pas si le nom de domaine de premier niveau est un nom de domaine valide répertorié dans la [base de données des zones racines de l’IANA](https://www.iana.org/domains/root/db). Cela nécessite une opération de recherche. À la place, l'expression régulière vérifie simplement que le nom de domaine de niveau supérieur comprend entre deux et vingt-quatre caractères ASCII, les premier et dernier caractères étant des caractères alphanumériques, les autres des caractères alphanumériques ou un trait d'union (-). 

```csharp
using System;
using System.Globalization;
using System.Text.RegularExpressions;

public class RegexUtilities
{
   bool invalid = false;

   public bool IsValidEmail(string strIn)
   {
       invalid = false;
       if (String.IsNullOrEmpty(strIn))
          return false;

       // Use IdnMapping class to convert Unicode domain names.
       try {
          strIn = Regex.Replace(strIn, @"(@)(.+)$", this.DomainMapper,
                                RegexOptions.None, TimeSpan.FromMilliseconds(200));
       }
       catch (RegexMatchTimeoutException) {
         return false;
       }

        if (invalid)
           return false;

       // Return true if strIn is in valid e-mail format.
       try {
          return Regex.IsMatch(strIn,
                @"^(?("")("".+?(?<!\\)""@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))" +
                @"(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-\w]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$",
                RegexOptions.IgnoreCase, TimeSpan.FromMilliseconds(250));
       }
       catch (RegexMatchTimeoutException) {
          return false;
       }
   }

   private string DomainMapper(Match match)
   {
      // IdnMapping class with default property values.
      IdnMapping idn = new IdnMapping();

      string domainName = match.Groups[2].Value;
      try {
         domainName = idn.GetAscii(domainName);
      }
      catch (ArgumentException) {
         invalid = true;
      }
      return match.Groups[1].Value + domainName;
   }
}
```

```vb
Imports System.Globalization
Imports System.Text.RegularExpressions

Public Class RegexUtilities
   Dim invalid As Boolean = False

   public Function IsValidEmail(strIn As String) As Boolean
       invalid = False
       If String.IsNullOrEmpty(strIn) Then Return False

       ' Use IdnMapping class to convert Unicode domain names.
       Try
          strIn = Regex.Replace(strIn, "(@)(.+)$", AddressOf Me.DomainMapper, 
                                RegexOptions.None, TimeSpan.FromMilliseconds(200))
       Catch e As RegexMatchTimeoutException
          Return False
       End Try

       If invalid Then Return False

       ' Return true if strIn is in valid e-mail format.
       Try
          Return Regex.IsMatch(strIn,
                 "^(?("")("".+?(?<!\\)""@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^`\{\}\|~\w])*)(?<=[0-9a-z])@))" +
                 "(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|(([0-9a-z][-\w]*[0-9a-z]*\.)+[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))$",
                 RegexOptions.IgnoreCase, TimeSpan.FromMilliseconds(250))
       Catch e As RegexMatchTimeoutException
          Return False
       End Try  
   End Function

   Private Function DomainMapper(match As Match) As String
      ' IdnMapping class with default property values.
      Dim idn As New IdnMapping()

      Dim domainName As String = match.Groups(2).Value
      Try
         domainName = idn.GetAscii(domainName)
      Catch e As ArgumentException
         invalid = True      
      End Try      
      Return match.Groups(1).Value + domainName
   End Function
End Class
```

Dans cet exemple, le modèle d'expression régulière `^(?(")(".+?(?<!\\)"@)|(([0-9a-z]((\.(?!\.))|[-!#\$%&'\*\+/=\?\^` \{ \} \|~ \w])*)(?<=[0-9a-z])@))(?(\[)(\[(\d{1,3}\.){3}\d{1,3}\])|( ([0-9 a-z] [-\w]*[0-9 a-z] *\.) + [a-z0-9] [\-a-z0-9]{0,22}[a-z0-9]))$` est interprété de la manière indiquée dans le tableau ci-dessous.Dans cet exemple, le modèle d’expression régulière. Notez que l’expression régulière est compilée à l’aide de l’indicateur [RegexOptions.IgnoreCase](xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase).

Modèle | Description
------- | ----------- 
`^` | Commence la recherche de correspondance au début de la chaîne.
`(?(")` | Détermine si le premier caractère est un guillemet. `(?(")` est le début d'une construction d'alternative.
`(?("")("".+?(?<!\\)""@)` | Si le premier caractère correspond à des guillemets, établit une correspondance avec des guillemets ouvrants suivis d'au moins une occurrence d'un caractère quelconque, suivie de guillemets fermants. Les guillemets fermants ne doivent pas être précédés d’une barre oblique inverse `(\). (?<!` est le début d’une assertion de postanalyse négative de largeur nulle. La chaîne doit se terminer par un arobase (@).
`&#124;(([0-9a-z] | Si le premier caractère n'est pas un guillemet, établit une correspondance avec un caractère alphabétique de a à z ou de A à Z (la comparaison ne respecte pas la casse) ou un chiffre (de 0 à 9).
`(\.(?!\.))` | Si le caractère suivant est un point, établit une correspondance avec un point. Dans le cas contraire, effectue une préanalyse du caractère suivant et continue la recherche de correspondances. `(?!\.)` est une assertion de préanalyse négative de largeur nulle qui empêche deux points consécutifs de s'afficher dans la partie locale d'une adresse de messagerie.
`&#124;[-!#\$%&'\*\+/=\?\^`\{\}\&#124;~\w] | Si le caractère suivant n’est pas un point, établit une correspondance avec un caractère alphabétique quelconque ou l’un des caractères suivants : -!#$%'*+=?^`{}&#124;~. 
`((\.(?!\.))&#124;[-!#\$%'\*\+/=\?\^`\{\}\&#124;~\w])* | Établit une correspondance avec le modèle d’alternative (un point suivi d’un autre caractère qu’un point, ou l’un des caractères) zéro, une ou plusieurs fois.
`@` | Correspond à l'arobase (@).
`(?<=[0-9a-z])` | Continue la recherche de correspondances si le caractère qui précède le caractère @ est compris entre A et Z, a et z, ou 0 et 9. La construction `(?<=[0-9a-z])` définit une assertion de postanalyse positive de largeur nulle.
`(?(\[)` | Vérifie si le caractère qui suit @ est un crochet ouvrant.
`(\[(\d{1,3}\.){3}\d{1,3}\])` | S'il s'agit d'un crochet ouvrant, établit une correspondance avec le crochet ouvrant suivi d'une adresse IP (quatre ensembles de un à trois chiffres, chaque ensemble étant séparé par un point) et d'un crochet fermant.
`&#124;(([0-9a-z][-\w]*[0-9a-z]*\.)+` | Si le caractère qui suit @ n'est pas un crochet ouvrant, établit une correspondance avec un caractère alphanumérique ayant une valeur comprise entre A et Z, a et z ou 0 et 9, suivi de zéro, une ou plusieurs occurrences d'un caractère alphabétique ou d'un trait d'union, suivi de zéro, un ou plusieurs caractères alphanumériques ayant une valeur comprise entre A et Z, a et z ou 0 et 9, suivi d'un point. Ce modèle peut être répété une ou plusieurs fois et doit être suivi du nom de domaine de niveau supérieur. 
`[a-z0-9][\-a-z0-9]{0,22}[a-z0-9]))` | Le nom de domaine de niveau supérieur doit commencer et se terminer par un caractère alphanumérique (compris entre a et z, A et Z ou 0 et 9). Il peut également comprendre entre zéro et 22 caractères ASCII (soit des caractères alphanumériques, soit des traits d'union). 
`$` | Termine la correspondance à la fin de la chaîne.
 
Vous pouvez appeler les méthodes `IsValidEmail` et `DomainMapper` en utilisant le code suivant :

```csharp
public class Application
{
   public static void Main()
   {
      RegexUtilities util = new RegexUtilities();
      string[] emailAddresses = { "david.jones@proseware.com", "d.j@server1.proseware.com",
                                  "jones@ms1.proseware.com", "j.@server1.proseware.com",
                                  "j@proseware.com9", "js#internal@proseware.com",
                                  "j_9@[129.126.118.1]", "j..s@proseware.com",
                                  "js*@proseware.com", "js@proseware..com",
                                  "js@proseware.com9", "j.s@server1.proseware.com",
                                   "\"j\\\"s\\\"\"@proseware.com", "js@contoso.中国" };

      foreach (var emailAddress in emailAddresses) {
         if (util.IsValidEmail(emailAddress))
            Console.WriteLine("Valid: {0}", emailAddress);
         else
            Console.WriteLine("Invalid: {0}", emailAddress);
      }                                            
   }
}
// The example displays the following output:
//       Valid: david.jones@proseware.com
//       Valid: d.j@server1.proseware.com
//       Valid: jones@ms1.proseware.com
//       Invalid: j.@server1.proseware.com
//       Valid: j@proseware.com9
//       Valid: js#internal@proseware.com
//       Valid: j_9@[129.126.118.1]
//       Invalid: j..s@proseware.com
//       Invalid: js*@proseware.com
//       Invalid: js@proseware..com
//       Valid: js@proseware.com9
//       Valid: j.s@server1.proseware.com
//       Valid: "j\"s\""@proseware.com
//       Valid: js@contoso.ä¸­å›½
```

```vb
Public Class Application
   Public Shared Sub Main()
      Dim util As New RegexUtilities()
      Dim emailAddresses() As String = { "david.jones@proseware.com", "d.j@server1.proseware.com", _
                                         "jones@ms1.proseware.com", "j.@server1.proseware.com", _
                                         "j@proseware.com9", "js#internal@proseware.com", _
                                         "j_9@[129.126.118.1]", "j..s@proseware.com", _
                                         "js*@proseware.com", "js@proseware..com", _
                                         "js@proseware.com9", "j.s@server1.proseware.com",
                                         """j\""s\""""@proseware.com", "js@contoso.中国" }

      For Each emailAddress As String In emailAddresses
         If util.IsValidEmail(emailAddress) Then
            Console.WriteLine("Valid: {0}", emailAddress)
         Else
            Console.WriteLine("Invalid: {0}", emailAddress)
         End If      
      Next                                            
   End Sub
End Class
' The example displays the following output:
'       Valid: david.jones@proseware.com
'       Valid: d.j@server1.proseware.com
'       Valid: jones@ms1.proseware.com
'       Invalid: j.@server1.proseware.com
'       Valid: j@proseware.com9
'       Valid: js#internal@proseware.com
'       Valid: j_9@[129.126.118.1]
'       Invalid: j..s@proseware.com
'       Invalid: js*@proseware.com
'       Invalid: js@proseware..com
'       Valid: js@proseware.com9
'       Valid: j.s@server1.proseware.com
'       Valid: "j\"s\""@proseware.com
'       Valid: js@contoso.ä¸­å›½
```

## <a name="see-also"></a>Voir aussi

[Expressions régulières .NET](regular-expressions.md)

[Exemples d’expressions régulières](regex-examples.md)

