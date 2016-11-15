---
title: "Bonnes pratiques pour l’utilisation de chaînes"
description: "Bonnes pratiques pour l’utilisation de chaînes"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b3cefaa4-0a3f-4a96-aba9-1de30fb07c29
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 3efd30bade564fe1b7dbf93237a9ff40c58c5f1e

---

# <a name="best-practices-for-using-strings"></a>Bonnes pratiques pour l’utilisation de chaînes

.NET offre une prise en charge complète du développement d’applications localisées et globalisées, et facilite l’application des conventions de la culture actuelle ou d’une culture spécifique lors de l’exécution d’opérations courantes telles que le tri et l’affichage de chaînes. Toutefois, le tri ou la comparaison de chaînes n'est pas toujours une opération dépendante de la culture. Par exemple, les chaînes utilisées en interne par une application doivent généralement être gérées de la même manière dans toutes les cultures. Quand des données de type chaîne culturellement indépendantes, telles que des étiquettes XML, des étiquettes HTML, des noms d’utilisateurs, des chemins d’accès aux fichiers et des noms d’objets système, sont interprétées comme si elles étaient dépendantes de la culture, le code d’application peut faire l’objet de bogues subtils, de performances médiocres et, dans certains cas, de problèmes de sécurité.

Cet article examine les méthodes de tri, de comparaison et d’application de la casse pour les chaînes dans .NET, présente des recommandations pour sélectionner une méthode appropriée de gestion des chaînes et fournit des informations supplémentaires sur les méthodes de gestion des chaînes. Elle décrit également comment les données mises en forme, telles que les données numériques et les données de date et d'heure, sont traitées pour l'affichage et pour le stockage. 

Cet article contient les sections suivantes :

* [Recommandations relatives à l’utilisation de chaînes](#recommendations-for-string-usage)

* [Spécification explicite de comparaisons de chaînes](#specifying-string-comparisons-explicitly)

* [Détails de la comparaison de chaînes](#the-details-of-string-comparison)

* [Choix d’un membre StringComparison pour votre appel de méthode](#choosing-a-stringcomparison-member-for-your-method-call)

* [Méthodes courantes de comparaison de chaînes](#common-string-comparison-methods)

* [Méthodes qui effectuent indirectement la comparaison de chaînes](#methods-that-perform-string-comparison-indirectly)

* [Affichage et persistance des données mises en forme](#displaying-and-persisting-formatted-data)

## <a name="recommendations-for-string-usage"></a>Recommandations relatives à l’utilisation de chaînes

Dans le cadre du développement à l’aide de .NET, suivez les recommandations simples ci-après quand vous utilisez des chaînes : 

* Utilisez des surcharges qui spécifient explicitement les règles de comparaison de chaînes pour les opérations de chaînes. Cela implique généralement l’appel d’une surcharge de méthode avec un paramètre de type [StringComparison](xref:System.StringComparison).

* Utilisez [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) pour les comparaisons et faites-en votre valeur par défaut sécurisée pour la mise en correspondance de chaînes de culture non spécifiée.

* Utilisez des comparaisons avec [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) pour atteindre de meilleures performances.

* Utilisez les opérations de chaînes basées sur [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) quand vous affichez la sortie à l’utilisateur.

* Utilisez des valeurs [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) non linguistiques plutôt que des opérations de chaînes basées sur [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) quand la comparaison est linguistiquement non pertinente (symbolique, par exemple).

* Utilisez la méthode [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) plutôt que la méthode [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) quand vous normalisez des chaînes à des fins de comparaison.

* Utilisez une surcharge de la méthode [String](xref:System.String) `Equals` pour tester si deux chaînes sont égales.

* Utilisez une surcharge des méthodes [String](xref:System.String) `Compare` et [String.CompareTo](xref:System.String.CompareTo(System.String)) pour trier des chaînes, et non pour en vérifier l’égalité.

* Utilisez la mise en forme en fonction de la culture pour afficher des données non-chaînées, telles que les nombres et les dates, dans une interface utilisateur. Utilisez la mise en forme en fonction de la culture dite indifférente pour rendre les données non-chaînées sous forme de chaîne.

Quand vous utilisez des chaînes, évitez les pratiques suivantes :

* N'utilisez pas de surcharges qui ne spécifient pas explicitement ou implicitement les règles de comparaison de chaînes pour les opérations de chaînes. 

* N’utilisez pas de surcharge de la méthode [String](xref:System.String) `Compare` ou [String.CompareTo](xref:System.String.CompareTo(System.String))et ne testez pas une valeur de retour de zéro pour déterminer si deux chaînes sont égales.

* N'utilisez pas la mise en forme qui tient compte de la culture pour rendre des données numériques ou les données de date et d'heure sous forme de chaîne.

## <a name="specifying-string-comparisons-explicitly"></a>Spécification explicite de comparaisons de chaînes

La plupart des méthodes de manipulation de chaînes dans .NET sont surchargées. Une ou plusieurs surcharges acceptent généralement des paramètres par défaut, contrairement à d'autres qui définissent avec précision la façon dont les chaînes doivent être comparées ou manipulées. La plupart des méthodes qui ne s’appuient pas sur des valeurs par défaut incluent un paramètre de type [StringComparison](xref:System.StringComparison), qui est une énumération spécifiant explicitement des règles pour la comparaison de chaînes selon la culture et la casse. Le tableau suivant décrit les membres de l’énumération [StringComparison](xref:System.StringComparison). 

Membre StringComparison | Description
----------------------- | -----------
[StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) | Effectue une comparaison respectant la casse à l'aide de la culture actuelle.
[CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) | Effectue une comparaison ne respectant pas la casse à l'aide de la culture actuelle.
[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) | Effectue une comparaison ordinale.
[StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) | Effectue une comparaison ordinale ne respectant pas la casse.

Par exemple, la méthode [String](xref:System.String) `IndexOf`, qui retourne l’index d’une sous-chaîne contenue dans un objet [String](xref:System.String) correspondant à un caractère ou à une chaîne, a neuf surcharges :

* [IndexOf(Char)](xref:System.String.IndexOf(System.Char)), [IndexOf(Char, Int32)](xref:System.String.IndexOf(System.Char,System.Int32)) et [IndexOf(Char, Int32, Int32)](xref:System.String.IndexOf(System.Char,System.Int32,System.Int32)), qui effectuent par défaut une recherche ordinale (respectant la casse et indépendante de la culture) d’un caractère dans la chaîne ;

* [IndexOf(String)](xref:System.String.IndexOf(System.String)), [IndexOf(String, Int32)](xref:System.String.IndexOf(System.String,System.Int32)) et [IndexOf(String, Int32, Int32)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32)), qui effectuent par défaut une recherche respectant la casse et dépendante de la culture d’une sous-chaîne dans la chaîne ;

* [IndexOf(String, StringComparison)](xref:System.String.IndexOf(System.String,System.StringComparison)), [IndexOf(String, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.StringComparison)) et [IndexOf(String, Int32, Int32, StringComparison)](xref:System.String.IndexOf(System.String,System.Int32,System.Int32,System.StringComparison)), qui incluent un paramètre de type StringComparison qui permet de spécifier la forme de la comparaison.

Nous vous recommandons de sélectionner une surcharge qui n'utilise pas de valeurs par défaut, pour les raisons suivantes :

* Certaines surcharges ayant des paramètres par défaut (celles qui recherchent un [Char](xref:System.Char) dans l’instance de chaîne) effectuent une comparaison ordinale, tandis que d’autres (celles qui recherchent une chaîne dans l’instance de chaîne) sont dépendantes de la culture. Il est difficile de mémoriser quelle méthode utilise quelle valeur par défaut, et les surcharges peuvent être facilement confondues.

* L'objectif du code qui s'appuie sur des valeurs par défaut pour les appels de méthode n'est pas clair. Dans l'exemple suivant, qui s'appuie sur des valeurs par défaut, il est difficile de savoir si le développeur voulait en fait une comparaison ordinale ou linguistique de deux chaînes, ou si une différence de casse entre `protocol` et "http" pourrait entraîner le retour de `false` par le test d'égalité.

  ```csharp
  string protocol = GetProtocol(url);       
  if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
     // ...Code to handle HTTP protocol.
  }
  else {
     throw new InvalidOperationException();
  }
  ```

  ```vb
  Dim protocol As String = GetProtocol(url)       
  If String.Equals(protocol, "http") Then
    ' ...Code to handle HTTP protocol.
  Else
     Throw New InvalidOperationException()
  End If
  ```

En général, nous vous recommandons d'appeler une méthode qui ne s'appuie pas sur des valeurs par défaut, car elle rend l'objectif du code non équivoque. Cela rend ensuite le code plus lisible et plus facile à déboguer et à gérer. L'exemple suivant aborde les questions soulevées à propos de l'exemple précédent. Il explique que la comparaison ordinale est utilisée et que les différences de casse sont ignorées. 

```csharp
string protocol = GetProtocol(url);       
if (String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase)) {
   // ...Code to handle HTTP protocol.
}
else {
   throw new InvalidOperationException();
}
```

```vb
Dim protocol As String = GetProtocol(url)       
If String.Equals(protocol, "http", StringComparison.OrdinalIgnoreCase) Then
   ' ...Code to handle HTTP protocol.
Else
   Throw New InvalidOperationException()
End If
```

## <a name="the-details-of-string-comparison"></a>Détails de la comparaison de chaînes

La comparaison de chaînes est le cœur de nombreuses opérations liées aux chaînes, en particulier le tri et le test d'égalité. Les chaînes sont triées dans un ordre déterminé : si "my" s'affiche avant "string" dans une liste triée de chaînes, "my" doit être considéré comme inférieur ou égal à "string". En outre, la comparaison définit implicitement l'égalité. L'opération de comparaison retourne zéro pour les chaînes qu'il estime égales. Considérer qu'aucune chaîne n'est inférieure à l'autre constitue une bonne interprétation. La plupart des opérations significatives impliquant des chaînes incluent l'une des procédures suivantes, ou les deux : comparaison avec une autre chaîne et exécution d'une opération de tri bien définie.

Toutefois, l'évaluation de l'égalité ou de l'ordre de tri de deux chaînes ne produit pas un résultat correct unique ; le résultat dépend des critères utilisés pour comparer les chaînes. En particulier, les comparaisons de chaînes qui sont ordinales ou basées sur les conventions de casse et de tri de la culture actuelle ou la culture dite indifférente (culture aux paramètres régionaux non spécifiés basée sur la langue anglaise) peuvent produire des résultats différents.

### <a name="string-comparisons-that-use-the-current-culture"></a>Comparaisons de chaînes qui utilisent la culture actuelle

L'un des critères à prendre en compte est l'utilisation des conventions de la culture actuelle lors de la comparaison de chaînes. Les comparaisons basées sur la culture actuelle utilisent la culture ou les paramètres régionaux actuels du thread. Vous devez toujours utiliser des comparaisons basées sur la culture actuelle quand les données sont linguistiquement pertinentes et quand elles reflètent l'intervention de l'utilisateur dépendante de la culture. 

Toutefois, le comportement de la comparaison et de la casse dans .NET change en fonction de la culture. Cela se produit quand une application s'exécute sur un ordinateur dont la culture est différente de celle de l'ordinateur sur lequel l'application a été développée, ou quand le thread en cours d'exécution change sa culture. Ce comportement est intentionnel, mais il reste peu évident à de nombreux développeurs. L'exemple suivant illustre les différences au niveau de l'ordre de tri entre les cultures Anglais (États-Unis) ("en-US") et Suédois ("sv-SE"). Notez que les mots « ångström », « Windows » et « Visual Studio » s’affichent à des positions différentes dans les tableaux de chaînes triées.

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string[] values= { "able", "ångström", "apple", "Æble", 
                         "Windows", "Visual Studio" };
      Array.Sort(values);
      DisplayArray(values);

      // Change culture to Swedish (Sweden).
      string originalCulture = CultureInfo.CurrentCulture.Name;
      Thread.CurrentThread.CurrentCulture = new CultureInfo("sv-SE");
      Array.Sort(values);
      DisplayArray(values);

      // Restore the original culture.
      Thread.CurrentThread.CurrentCulture = new CultureInfo(originalCulture);
    }

    private static void DisplayArray(string[] values)
    {
      Console.WriteLine("Sorting using the {0} culture:",  
                        CultureInfo.CurrentCulture.Name);
      foreach (string value in values)
         Console.WriteLine("   {0}", value);

      Console.WriteLine();
    }
}
// The example displays the following output:
//       Sorting using the en-US culture:
//          able
//          Æble
//          ångström
//          apple
//          Visual Studio
//          Windows
//       
//       Sorting using the sv-SE culture:
//          able
//          Æble
//          apple
//          Windows
//          Visual Studio
//          ångström
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim values() As String = { "able", "ångström", "apple", _
                                 "Æble", "Windows", "Visual Studio" }
      Array.Sort(values)
      DisplayArray(values)

      ' Change culture to Swedish (Sweden).
      Dim originalCulture As String = CultureInfo.CurrentCulture.Name
      Thread.CurrentThread.CurrentCulture = New CultureInfo("sv-SE")
      Array.Sort(values)
      DisplayArray(values)

      ' Restore the original culture.
      Thread.CurrentThread.CurrentCulture = New CultureInfo(originalCulture)
    End Sub

    Private Sub DisplayArray(values() As String)
      Console.WRiteLine("Sorting using the {0} culture:", _ 
                        CultureInfo.CurrentCulture.Name)
      For Each value As String In values
         Console.WriteLine("   {0}", value)
      Next
      Console.WriteLine()   
    End Sub
End Module
' The example displays the following output:
'       Sorting using the en-US culture:
'          able
'          Æble
'          ångström
'          apple
'          Visual Studio
'          Windows
'       
'       Sorting using the sv-SE culture:
'          able
'          Æble
'          apple
'          Windows
'          Visual Studio
'          ångström
```

Les comparaisons ne respectant pas la casse qui utilisent la culture actuelle sont identiques aux comparaisons dépendantes de la culture, mais elles ignorent la casse, comme défini par la culture actuelle du thread. Ce comportement peut également se manifester dans les ordres de tri. 

Les comparaisons qui utilisent la sémantique de la culture actuelle sont la valeur par défaut pour les méthodes suivantes :

* surcharges [String](xref:System.String) `Compare` qui n’incluent pas de paramètre [StringComparison](xref:System.StringComparison) ;

* surcharges [String.CompareTo](xref:System.String.CompareTo(System.String)) ;

* méthode [String.StartsWith(String)](xref:System.String.StartsWith(System.String)) par défaut ; 

* méthode [String.EndsWith(String)](xref:System.String.EndsWith(System.String)) par défaut ;

* surcharges [String](xref:System.String) `IndexOf` qui acceptent un [String](xref:System.String) en tant que paramètre de recherche et qui n’ont pas de paramètre [StringComparison](xref:System.StringComparison).

* surcharges [String](xref:System.String) `LastIndexOf` qui acceptent un [String](xref:System.String) comme paramètre de recherche et qui n’ont pas de paramètre [StringComparison](xref:System.StringComparison).

Dans tous les cas, nous vous recommandons d’appeler une surcharge qui a un paramètre [StringComparison](xref:System.StringComparison) pour que l’objectif de l’appel de la méthode soit clair. 

Des bogues, plus ou moins subtils, peuvent émerger quand des données de type chaîne non linguistiques sont interprétées linguistiquement, ou quand des données de type chaîne d'une culture particulière sont interprétées à l'aide des conventions d'une autre culture. L'exemple canonique est le problème du caractère I en turc.

Dans presque tous les alphabets latins, y compris l'anglais (États-Unis), le caractère "i" (\u0069) est la version en minuscule du caractère "I" (\u0049). Cette règle de casse devient rapidement la valeur par défaut pour quelqu'un qui effectue de la programmation dans une telle culture. Toutefois, l’alphabet turc ("tr-TR") inclut un caractère "I avec un point", "İ" (\u0130), qui est la version en majuscule de "i". Le turc comprend également un caractère "i sans point" minuscule, "ı" (\u0131), dont la majuscule est "I". Ce comportement se produit également dans la culture azérie ("az").

Par conséquent, les suppositions faites sur la mise en majuscule du "i" ou de la mise en minuscule du "I" ne sont pas valides dans toutes les cultures. Si vous utilisez les surcharges par défaut pour les routines de comparaison de chaînes, elles varieront suivant les cultures. Si les données à comparer sont non linguistiques, l'utilisation de surcharges par défaut peut produire des résultats indésirables, comme le montre la tentative suivante d'exécution d'une comparaison ne respectant pas la casse des chaînes "file" et "FILE".

```csharp
using System;
using System.Globalization;
using System.Threading;

public class Example
{
   public static void Main()
   {
      string fileUrl = "file";
      Thread.CurrentThread.CurrentCulture = new CultureInfo("en-US");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                       fileUrl.StartsWith("FILE", true, null));
      Console.WriteLine();

      Thread.CurrentThread.CurrentCulture = new CultureInfo("tr-TR");
      Console.WriteLine("Culture = {0}",
                        Thread.CurrentThread.CurrentCulture.DisplayName);
      Console.WriteLine("(file == FILE) = {0}", 
                        fileUrl.StartsWith("FILE", true, null));
   }
}
// The example displays the following output:
//       Culture = English (United States)
//       (file == FILE) = True
//       
//       Culture = Turkish (Turkey)
//       (file == FILE) = False
```

```vb
Imports System.Globalization
Imports System.Threading

Module Example
   Public Sub Main()
      Dim fileUrl = "file"
      Thread.CurrentThread.CurrentCulture = New CultureInfo("en-US")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                       fileUrl.StartsWith("FILE", True, Nothing))
      Console.WriteLine()

      Thread.CurrentThread.CurrentCulture = New CultureInfo("tr-TR")
      Console.WriteLine("Culture = {0}", _
                        Thread.CurrentThread.CurrentCulture.DisplayName)
      Console.WriteLine("(file == FILE) = {0}", _ 
                        fileUrl.StartsWith("FILE", True, Nothing))
   End Sub
End Module
' The example displays the following output:
'       Culture = English (United States)
'       (file == FILE) = True
'       
'       Culture = Turkish (Turkey)
'       (file == FILE) = False
```

Cette comparaison peut provoquer de sérieux problèmes si la culture est utilisée par inadvertance dans des paramètres de sécurité sensibles, comme dans l'exemple suivant. Un appel de méthode tel que `IsFileURI("file:")` retourne la valeur `true` si la culture actuelle est Anglais (États-Unis), mais `false` si la culture actuelle est Turc. Par conséquent, sur les systèmes turcs, quelqu'un pourrait contourner les mesures de sécurité qui bloquent l'accès aux URI ne respectant pas la casse qui commencent par "FILE:".

```csharp
public static bool IsFileURI(String path) 
{
   return path.StartsWith("FILE:", true, null);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
   Return path.StartsWith("FILE:", True, Nothing)
End Function
```

Dans ce cas, étant donné que "file:" doit être interprété comme un identificateur non linguistique indépendant de la culture, le code doit plutôt être écrit comme indiqué dans l'exemple suivant.

```csharp
public static bool IsFileURI(string path) 
{
   return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase);
}
```

```vb
Public Shared Function IsFileURI(path As String) As Boolean 
    Return path.StartsWith("FILE:", StringComparison.OrdinalIgnoreCase)
End Function
```

## <a name="ordinal-string-operations"></a>Opérations de chaînes ordinales

La spécification de la valeur [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) ou [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) dans un appel de méthode signifie une comparaison non linguistique dans laquelle les fonctionnalités linguistiques naturelles sont ignorées. Les méthodes qui sont appelées avec ces valeurs [StringComparison](xref:System.StringComparison) font reposer les décisions d’opération de chaîne sur de simples comparaisons d’octets plutôt que sur la casse ou des tables d’équivalences paramétrables par la culture. Dans la plupart des cas, cette approche correspond le mieux à l'interprétation de chaînes prévue tout en rendant le code plus rapide et plus fiable. 

Les comparaisons ordinales sont des comparaisons de chaînes dans lesquelles chaque octet de chaque chaîne est comparé sans interprétation linguistique ; par exemple, "windows" ne correspond pas à "Windows". Utilisez cette comparaison quand le contexte indique que les chaînes doivent correspondre exactement ou demande une stratégie de correspondance classique. En outre, la comparaison ordinale est l'opération de comparaison la plus rapide, car elle n'applique aucune règle linguistique lors de la détermination d'un résultat.

Les chaînes dans .NET peuvent contenir des caractères Null incorporés. L'une des différences les plus évidentes entre la comparaison ordinale et la comparaison dépendante de la culture (y compris les comparaisons qui utilisent la culture dite indifférente) concerne la gestion des caractères Null incorporés dans une chaîne. Ces caractères sont ignorés quand vous utilisez les méthodes [String](xref:System.String) `Compare` et [String](xref:System.String) `Equals` pour effectuer des comparaisons dépendantes de la culture (notamment des comparaisons qui utilisent la culture dite indifférente). Par conséquent, dans les comparaisons dépendantes de la culture, les chaînes qui contiennent des caractères Null incorporés peuvent être considérées comme égales à des chaînes qui n'en contiennent pas. 

> [!IMPORTANT]
> Bien que les méthodes de comparaison de chaînes ignorent les caractères Null incorporés, les méthodes de recherche de chaîne comme [String.Contains](xref:System.String.Contains(System.String)), [String.EndsWith](xref:System.String.EndsWith(System.String)), [String.IndexOf](xref:System.String.IndexOf(System.Char)), [String.LastIndexOf](xref:System.String.LastIndexOf(System.String)) et [String.StartsWith](xref:System.String.StartsWith(System.String)) ne les ignorent pas. 

L'exemple suivant effectue une comparaison dépendante de la culture de la chaîne "Aa" avec une chaîne semblable qui contient plusieurs caractères Null incorporés entre "A" et "a", et montre comment les deux chaînes sont considérées comme égales. 

```csharp
using System;

public class Example
{
   public static void Main()
   {
      string str1 = "Aa";
      string str2 = "A" + new String('\u0000', 3) + "a";
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                        str1, ShowBytes(str1), str2, ShowBytes(str2));
      Console.WriteLine("   With String.Compare:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Compare(str1, str2, StringComparison.InvariantCulture));

      Console.WriteLine("   With String.Equals:");
      Console.WriteLine("      Current Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.CurrentCulture));
      Console.WriteLine("      Invariant Culture: {0}", 
                        String.Equals(str1, str2, StringComparison.InvariantCulture));
   }

   private static string ShowBytes(string str)
   {
      string hexString = String.Empty;
      for (int ctr = 0; ctr < str.Length; ctr++)
      {
         string result = String.Empty;
         result = Convert.ToInt32(str[ctr]).ToString("X4");
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2);
         hexString += result;
      }
      return hexString.Trim();
   }
}
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Current Culture: 0
//          Invariant Culture: 0
//       With String.Equals:
//          Current Culture: True
//          Invariant Culture: True
```

```vb
Module Example
   Public Sub Main()
      Dim str1 As String = "Aa"
      Dim str2 As String = "A" + New String(Convert.ToChar(0), 3) + "a"
      Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                        str1, ShowBytes(str1), str2, ShowBytes(str2))
      Console.WriteLine("   With String.Compare:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Compare(str1, str2, StringComparison.InvariantCulture))

      Console.WriteLine("   With String.Equals:")
      Console.WriteLine("      Current Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.CurrentCulture))
      Console.WriteLine("      Invariant Culture: {0}", _
                        String.Equals(str1, str2, StringComparison.InvariantCulture))
   End Sub

   Private Function ShowBytes(str As String) As String
      Dim hexString As String = String.Empty
      For ctr As Integer = 0 To str.Length - 1
         Dim result As String = String.Empty
         result = Convert.ToInt32(str.Chars(ctr)).ToString("X4")
         result = " " + result.Substring(0,2) + " " + result.Substring(2, 2)
         hexString += result
      Next
      Return hexString.Trim()
   End Function
End Module
```

Toutefois, les chaînes ne sont pas considérées comme égales quand vous utilisez la comparaison ordinale, comme le montre l'exemple suivant.

```csharp
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", 
                  str1, ShowBytes(str1), str2, ShowBytes(str2));
Console.WriteLine("   With String.Compare:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Compare(str1, str2, StringComparison.Ordinal));

Console.WriteLine("   With String.Equals:");
Console.WriteLine("      Ordinal: {0}", 
                  String.Equals(str1, str2, StringComparison.Ordinal));
// The example displays the following output:
//    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
//       With String.Compare:
//          Ordinal: 97
//       With String.Equals:
//          Ordinal: False
```

```vb
Console.WriteLine("Comparing '{0}' ({1}) and '{2}' ({3}):", _
                  str1, ShowBytes(str1), str2, ShowBytes(str2))
Console.WriteLine("   With String.Compare:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Compare(str1, str2, StringComparison.Ordinal))

Console.WriteLine("   With String.Equals:")
Console.WriteLine("      Ordinal: {0}", _
                  String.Equals(str1, str2, StringComparison.Ordinal))
' The example displays the following output:
'    Comparing 'Aa' (00 41 00 61) and 'A   a' (00 41 00 00 00 00 00 00 00 61):
'       With String.Compare:
'          Ordinal: 97
'       With String.Equals:
'          Ordinal: False
```

Les comparaisons ordinales ne respectant pas la casse sont l'approche la plus conservatrice suivante. Ces comparaisons ignorent la plus grande partie de la casse ; par exemple, "windows" correspond à "Windows". Lors du traitement de caractères ASCII, cette stratégie est équivalente à [StringComparison.Ordinal](xref:System.StringComparison.Ordinal), excepté qu’elle ignore la casse ASCII habituelle. Par conséquent, tout caractère de la plage [A, Z] (\u0041-\u005A) correspond au caractère correspondant de la plage [a,z] (\u0061-\007A). La casse hors de la plage ASCII utilise les tables de la culture dite indifférente. Par conséquent, la comparaison suivante :

```csharp
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase);
```

```vb
String.Compare(strA, strB, StringComparison.OrdinalIgnoreCase)
```

est équivalente à la comparaison suivante (mais plus rapide) : 

```csharp
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal);
```

```vb
String.Compare(strA.ToUpperInvariant(), strB.ToUpperInvariant(), 
               StringComparison.Ordinal)
```

Ces comparaisons restent très rapides.

[StringComparison.Ordinal](xref:System.StringComparison.Ordinal) et [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) utilisent les valeurs binaires directement et conviennent mieux à la mise en correspondance. Quand vous n'êtes pas sûr de vos paramètres de comparaison, utilisez l'une de ces deux valeurs. Toutefois, étant donné qu'elles effectuent une comparaison octet par octet, elles n'effectuent pas le tri selon un ordre de tri linguistique (comme un dictionnaire français), mais selon un ordre de tri binaire. Les résultats peuvent sembler étranges dans la plupart des contextes s'ils sont affichés aux utilisateurs.

La sémantique ordinale est la valeur par défaut pour les surcharges [String](xref:System.String) `Equals` qui n’incluent pas d’argument [StringComparison](xref:System.StringComparison) (notamment l’opérateur d’égalité). Dans tous les cas, nous vous recommandons d’appeler une surcharge ayant un paramètre [StringComparison](xref:System.StringComparison).

### <a name="string-operations-that-use-the-invariant-culture"></a>Opérations de chaîne qui utilisent la culture dite indifférente

Les comparaisons avec la culture dite indifférente utilisent la propriété [CompareInfo](xref:System.Globalization.CompareInfo) retournée par la méthode [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) statique. Ce comportement est le même sur tous les systèmes ; il traduit tous les caractères en dehors de sa plage en ce qu'il suppose être des caractères invariants équivalents. Cette stratégie peut être utile pour la gestion d'un jeu de comportements de chaîne dans toutes les cultures, mais elle donne souvent des résultats inattendus.

Les comparaisons ne respectant pas la casse avec la culture dite indifférente utilisent la propriété [CompareInfo](xref:System.Globalization.CompareInfo) statique retournée par la propriété [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) statique pour les informations de comparaison également. Toutes les différences de casse entre ces caractères traduits sont ignorées.

L’objet [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) entraîne l’interprétation par la méthode [String](xref:System.String) `Compare` de certains jeux de caractères comme étant équivalents. Par exemple, l'équivalence suivante est valide dans la culture dite indifférente :

InvariantCulture: a + ̊ = å

Le caractère Lettre minuscule latine A "a" (\u0061), quand il se trouve à côté du caractère diacritique rond en chef "+ " ̊" (\u030a), est interprété comme une lettre minuscule latine A avec diacritique rond en chef "å" (\u00e5). Comme le montre l'exemple suivant, ce comportement diffère de la comparaison ordinale.

```csharp
string separated = "\u0061\u030a";
string combined = "\u00e5";

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}",
                  separated, combined, 
                  String.Compare(separated, combined, 
                                 StringComparison.InvariantCulture) == 0);

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}",
                  separated, combined,
                  String.Compare(separated, combined, 
                                 StringComparison.Ordinal) == 0);
// The example displays the following output:
//    Equal sort weight of a° and å using InvariantCulture: True
//    Equal sort weight of a° and å using Ordinal: False 
```

```vb
Dim separated As String = ChrW(&h61) + ChrW(&h30a)
Dim combined As String = ChrW(&he5)

Console.WriteLine("Equal sort weight of {0} and {1} using InvariantCulture: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _ 
                                 StringComparison.InvariantCulture) = 0)

Console.WriteLine("Equal sort weight of {0} and {1} using Ordinal: {2}", _
                  separated, combined, _
                  String.Compare(separated, combined, _
                                 StringComparison.Ordinal) = 0)
' The example displays the following output:
'    Equal sort weight of a° and å using InvariantCulture: True
'    Equal sort weight of a° and å using Ordinal: False
```

Lors de l’interprétation de noms de fichiers, de cookies ou de tout autre élément dans lequel peut s’afficher une combinaison telle que "å", les comparaisons ordinales offrent toujours le comportement le plus transparent et le plus approprié.

En définitive, la culture dite indifférente a très peu de propriétés qui la rendent utile pour la comparaison. Elle effectue la comparaison d'une manière linguistiquement pertinente, qui l'empêche de garantir une équivalence symbolique complète, mais elle ne constitue pas le choix approprié pour l'affichage dans n'importe quelle culture. Par exemple, si un fichier de données volumineux qui contient une liste d'identificateurs triés à des fins d'affichage accompagne une application, un ajout à cette liste nécessiterait une insertion avec un tri de style invariant.

## <a name="choosing-a-stringcomparison-member-for-your-method-call"></a>Choix d’un membre StringComparison pour votre appel de méthode

Le tableau suivant décrit le mappage entre le contexte de chaîne sémantique et un membre de l’énumération [StringComparison](xref:System.StringComparison).

Données | Comportement | Valeur System.StringComparison correspondante
---- | -------- | -------------------------------------------
Identificateurs internes respectant la casse, identificateurs respectant la casse dans des normes telles que XML et HTTP ou paramètres liés à la sécurité respectant la casse. | Identificateur non linguistique, où les octets correspondent exactement. | [StringComparison.Ordinal](xref:System.StringComparison.Ordinal)
Identificateurs internes ne respectant pas la casse, identificateurs ne respectant pas la casse dans des normes telles que XML et HTTP, chemins de fichiers, clés et valeurs de Registre, variables d’environnement, identificateurs de ressources (par exemple, noms de handle) ou paramètres liés à la sécurité ne respectant pas la casse. | Identificateur non linguistique, où la casse est sans importance. | [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase)
Données affichées à l’utilisateur ou la plupart des entrées d’utilisateur. | Données qui nécessitent des usages linguistiques locaux. | [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture) ou [CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase)

## <a name="common-string-comparison-methods"></a>Méthodes courantes de comparaison de chaînes

Les sections suivantes décrivent les méthodes le plus souvent utilisées pour la comparaison de chaînes.

### <a name="stringcompare"></a>String.Compare

Interprétation par défaut : [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

En tant qu'opération la plus centrale de l'interprétation de chaînes, toutes les instances de ces appels de méthode doivent être examinées pour déterminer si les chaînes doivent être interprétées d'après la culture actuelle ou être dissociées de la culture (symboliquement). En général, il s’agit de la dernière et une comparaison [StringComparison.Ordinal](xref:System.StringComparison.Ordinal) doit plutôt être utilisée.

La classe [System.Globalization.CompareInfo](xref:System.Globalization.CompareInfo), retournée par la propriété [CultureInfo.CompareInfo](xref:System.Globalization.CultureInfo.CompareInfo), inclut également une méthode [Compare](xref:System.Globalization.CompareInfo.Compare(System.String,System.Int32,System.String,System.Int32,System.Globalization.CompareOptions)) qui fournit un grand nombre d’options de mise en correspondance (ordinale, ignorant les espaces blancs, ignorant le type kana, etc.) au moyen de l’énumération d’indicateur [CompareOptions](xref:System.Globalization.CompareOptions). 

### <a name="stringcompareto"></a>String.CompareTo

Interprétation par défaut : [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Cette méthode n’offre actuellement pas de surcharge spécifiant un type [StringComparison](xref:System.StringComparison). Il est généralement possible de convertir cette méthode dans la forme [String.Compare(String, String, StringComparison)](xref:System.String.Compare(System.String,System.String,System.StringComparison)) recommandée.

Les types qui implémentent les interfaces [IComparable](xref:System.IComparable) et [IComparable&lt;T&gt;](xref:System.IComparable%601) implémentent cette méthode. Étant donné qu’elle n’offre pas la possibilité d’un paramètre [StringComparison](xref:System.StringComparison), les types d’implémentation permettent souvent à l’utilisateur de spécifier un [StringComparer](xref:System.StringComparer) dans leur constructeur. L’exemple suivant définit une classe `FileName` dont le constructeur de classe inclut un paramètre [StringComparer](xref:System.StringComparer). Cet objet [StringComparer](xref:System.StringComparer) est alors utilisé dans la méthode `FileName.CompareTo`.

```csharp
using System;

public class FileName : IComparable
{
   string fname;
   StringComparer comparer; 

   public FileName(string name, StringComparer comparer)
   {
      if (String.IsNullOrEmpty(name))
         throw new ArgumentNullException("name");

      this.fname = name;

      if (comparer != null)
         this.comparer = comparer;
      else
         this.comparer = StringComparer.OrdinalIgnoreCase;
   }

   public string Name
   {
      get { return fname; }
   }

   public int CompareTo(object obj)
   {
      if (obj == null) return 1;

      if (! (obj is FileName))
         return comparer.Compare(this.fname, obj.ToString());
      else
         return comparer.Compare(this.fname, ((FileName) obj).Name);
   }
}
```

```vb
Public Class FileName : Implements IComparable
   Dim fname As String
   Dim comparer As StringComparer 

   Public Sub New(name As String, comparer As StringComparer)
      If String.IsNullOrEmpty(name) Then
         Throw New ArgumentNullException("name")
      End If

      Me.fname = name

      If comparer IsNot Nothing Then
         Me.comparer = comparer
      Else
         Me.comparer = StringComparer.OrdinalIgnoreCase
      End If      
   End Sub

   Public ReadOnly Property Name As String
      Get
         Return fname
      End Get   
   End Property

   Public Function CompareTo(obj As Object) As Integer _
          Implements IComparable.CompareTo
      If obj Is Nothing Then Return 1

      If Not TypeOf obj Is FileName Then
         obj = obj.ToString()
      Else
         obj = CType(obj, FileName).Name
      End If         
      Return comparer.Compare(Me.fname, obj)
   End Function
End Class
```

### <a name="stringequals"></a>String.Equals

Interprétation par défaut : [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).

La classe [String](xref:System.String) vous permet de tester l’égalité en appelant les surcharges de la méthode `Equals` statique ou d’instance, ou en utilisant l’opérateur d’égalité statique. Par défaut, les surcharges et l'opérateur utilisent la comparaison ordinale. Toutefois, nous vous recommandons quand même d’appeler une surcharge qui spécifie explicitement le type [StringComparison](xref:System.StringComparison), même si vous voulez effectuer une comparaison ordinale ; cela simplifie la recherche d’une interprétation de chaîne particulière dans du code. 

### <a name="stringtoupper-and-stringtolower"></a>String.ToUpper et String.ToLower

Interprétation par défaut : [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Vous devez faire preuve de prudence quand vous utilisez ces méthodes, car imposer une majuscule ou une minuscule dans une chaîne est souvent utilisé comme une petite normalisation pour la comparaison de chaînes indépendamment de la casse. Si tel est le cas, vous devez envisager d'utiliser une comparaison ne respectant pas la casse. 

Les méthodes [String.ToUpperInvariant](xref:System.String.ToUpperInvariant) et [String.ToLowerInvariant](xref:System.String.ToLowerInvariant) sont également disponibles. [ToUpperInvariant](xref:System.String.ToUpperInvariant) est le moyen standard de normaliser la casse. Les comparaisons faites à l’aide de [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) se composent sur le plan comportemental de deux appels : appel à [ToUpperInvariant](xref:System.String.ToUpperInvariant) sur les deux arguments de chaîne et comparaison à l’aide de [StringComparison.Ordinal](xref:System.StringComparison.Ordinal).

Des surcharges sont également disponibles pour la conversion en majuscules et en minuscules dans une culture spécifique, en passant à la méthode un objet [CultureInfo](xref:System.Globalization.CultureInfo) qui représente cette culture.

### <a name="chartoupper-and-chartolower"></a>Char.ToUpper et Char.ToLower

Interprétation par défaut : [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Ces méthodes fonctionnent de façon similaire aux méthodes [String.ToUpper](xref:System.String.ToUpper) et [String.ToLower](xref:System.String.ToLower) décrites dans la section précédente.

### <a name="stringstartswith-and-stringendswith"></a>String.StartsWith et String.EndsWith

Interprétation par défaut : [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Par défaut, ces deux méthodes effectuent une comparaison dépendante de la culture.

### <a name="stringindexof-and-stringlastindexof"></a>String.IndexOf et String.LastIndexOf

Interprétation par défaut : [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

La façon dont les surcharges par défaut de ces méthodes effectuent les comparaisons n'est pas cohérente. Toutes les méthodes [String](xref:System.String) `IndexOf` et [String](xref:System.String) `LastIndexOf` qui incluent un paramètre [Char](xref:System.Char) effectuent une comparaison ordinale, mais les méthodes [String](xref:System.String) `IndexOf` et [String`](xref:System.String) `LastIndexOf` par défaut qui incluent un paramètre [String](xref:System.String) effectuent une comparaison dépendante de la culture. 

Si vous appelez la méthode ` `IndexOf` or `LastIndexOf` et que vous lui passez une chaîne à localiser dans l’instance actuelle, nous vous recommandons d’appeler une surcharge qui spécifie explicitement le type [StringComparison](xref:System.StringComparison). Les surcharges qui incluent un argument [Char](xref:System.Char) ne vous permettent pas de spécifier un type [StringComparison](xref:System.StringComparison).

## <a name="methods-that-perform-string-comparison-indirectly"></a>Méthodes qui effectuent indirectement la comparaison de chaînes

Certaines méthodes autres que les méthodes de chaîne dont l’opération centrale est la comparaison de chaînes utilisent le type [StringComparer](xref:System.StringComparer). La classe [StringComparer](xref:System.StringComparer) inclut quatre propriétés statiques qui retournent des instances de [StringComparer](xref:System.StringComparer) dont les méthodes `Compare` effectuent les types de comparaisons de chaînes suivants :

* Comparaisons de chaînes dépendantes de la culture à l'aide de la culture actuelle. Cet objet [StringComparer](xref:System.StringComparer) est retourné par la propriété [StringComparer.CurrentCulture](xref:System.StringComparer.CurrentCulture).

* Comparaisons ne respectant pas la casse à l'aide de la culture actuelle. Cet objet [StringComparer](xref:System.StringComparer) est retourné par la propriété [StringComparer.CurrentCultureIgnoreCase](xref:System.StringComparer.CurrentCultureIgnoreCase).

* Comparaison ordinale. Cet objet [StringComparer](xref:System.StringComparer) est retourné par la propriété [StringComparer.Ordinal](xref:System.StringComparer.Ordinal). 

* Comparaison ordinale ne respectant pas la casse. Cet objet [StringComparer](xref:System.StringComparer) est retourné par la propriété [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase).

### <a name="arraysort-and-arraybinarysearch"></a>Array.Sort et Array.BinarySearch

Interprétation par défaut : [StringComparison.CurrentCulture](xref:System.StringComparison.CurrentCulture).

Quand vous stockez des données dans une collection ou quand vous lisez des données persistantes à partir d’un fichier ou d’une base de données dans une collection, le changement de culture actuelle peut invalider les invariants de la collection. La méthode [Array.BinarySearch](xref:System.Array.BinarySearch(System.Array,System.Object)) suppose que les éléments du tableau dans lequel effectuer la recherche sont déjà triés. Pour trier tout élément de chaîne dans le tableau, la méthode [Array.Sort](xref:System.Array.Sort(System.Array)) appelle la méthode [String] `Compare` pour classer les éléments individuels. L'utilisation d'un comparateur dépendant de la culture peut s'avérer dangereux si la culture change entre le moment où le tableau est trié et le moment où son contenu fait l'objet d'une recherche. Par exemple, dans le code suivant, le stockage et la récupération fonctionnent sur le comparateur fourni implicitement par la propriété `Thread.CurrentThread.CurrentCulture`. Si la culture peut changer entre les appels à `StoreNames` et `DoesNameExist`, et surtout si le contenu du tableau est rendu persistant à un moment donné entre les deux appels de méthode, la recherche binaire peut échouer. 

```csharp
// Incorrect.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names); // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name) >= 0);  // Line B.
}
```

```vb
' Incorrect.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names)          ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name) >= 0      ' Line B.
End Function
```

L'exemple suivant, qui utilise la même méthode de comparaison ordinale (indépendante de la culture) pour trier le tableau et pour effectuer une recherche, présente une variation recommandée. Le code de modification est reflété dans les lignes libellées `Line A` et `Line B` dans les deux exemples.

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.Ordinal);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.Ordinal) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.Ordinal)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.Ordinal) >= 0      ' Line B.
End Function
```

Si ces données sont rendues persistantes et déplacées dans toutes les cultures, et que le tri est utilisé pour présenter ces données à l'utilisateur, vous pouvez envisager d'utiliser `StringComparison.InvariantCulture`, qui fonctionne linguistiquement pour une meilleure sortie d'utilisateur mais n'est pas affecté par les modifications apportées à la culture. L'exemple suivant modifie les deux exemples précédents pour utiliser la culture dite indifférente pour le tri du tableau et la recherche dans celui-ci.

```csharp
// Correct.
string []storedNames;

public void StoreNames(string [] names)
{
   int index = 0;
   storedNames = new string[names.Length];

   foreach (string name in names)
   {
      this.storedNames[index++] = name;
   }

   Array.Sort(names, StringComparer.InvariantCulture);  // Line A.
}

public bool DoesNameExist(string name)
{
   return (Array.BinarySearch(this.storedNames, name, StringComparer.InvariantCulture) >= 0);  // Line B.
}
```

```vb
' Correct.
Dim storedNames() As String

Public Sub StoreNames(names() As String)
   Dim index As Integer = 0
   ReDim storedNames(names.Length - 1)

   For Each name As String In names
      Me.storedNames(index) = name
      index+= 1
   Next

   Array.Sort(names, StringComparer.InvariantCulture)           ' Line A.
End Sub

Public Function DoesNameExist(name As String) As Boolean
   Return Array.BinarySearch(Me.storedNames, name, StringComparer.InvariantCulture) >= 0      ' Line B.
End Function
```

### <a name="collections-example-hashtable-constructor"></a>Exemple de collections : constructeur Hashtable

Le hachage de chaînes constitue un deuxième exemple d'opération qui est affectée par la façon dont des chaînes sont comparées. 

L’exemple suivant instancie un objet [Hashtable](xref:System.Collections.Hashtable) en lui passant l’objet [StringComparer](xref:System.StringComparer) qui est retourné par la propriété [StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase). Étant donné qu’une classe [StringComparer](xref:System.StringComparer) dérivée de [StringComparer](xref:System.StringComparer) implémente l’interface [IEqualityComparer](xref:System.Collections.IEqualityComparer), sa méthode [GetHashCode](xref:System.Collections.IEqualityComparer) est utilisée pour calculer le code de hachage des chaînes dans la table de hachage.

```csharp
const int initialTableCapacity = 100;
Hashtable h;

public void PopulateFileTable(string directory)
{
   h = new Hashtable(initialTableCapacity, 
                     StringComparer.OrdinalIgnoreCase);

   foreach (string file in Directory.GetFiles(directory))
         h.Add(file, File.GetCreationTime(file));
}

public void PrintCreationTime(string targetFile)
{
   Object dt = h[targetFile];
   if (dt != null)
   {
      Console.WriteLine("File {0} was created at time {1}.",
         targetFile, 
         (DateTime) dt);
   }
   else
   {
      Console.WriteLine("File {0} does not exist.", targetFile);
   }
}
```

```vb
Const initialTableCapacity As Integer = 100
Dim h As Hashtable

Public Sub PopulateFileTable(dir As String)
   h = New Hashtable(initialTableCapacity, _
                     StringComparer.OrdinalIgnoreCase)

   For Each filename As String In Directory.GetFiles(dir)
      h.Add(filename, File.GetCreationTime(filename))
   Next                        
End Sub

Public Sub PrintCreationTime(targetFile As String)
   Dim dt As Object = h(targetFile)
   If dt IsNot Nothing Then
      Console.WriteLine("File {0} was created at {1}.", _
         targetFile, _
         CDate(dt))
   Else
      Console.WriteLine("File {0} does not exist.", targetFile)
   End If
End Sub  
```

## <a name="displaying-and-persisting-formatted-data"></a>Affichage et persistance des données mises en forme

Lorsque vous affichez des données non-chaînées telles que les nombres et les dates et heures aux utilisateurs, mettez-les en forme en utilisant les paramètres de la culture de l'utilisateur. Par défaut, la méthode [String.Format](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) et les méthodes `ToString` des types numériques et des types de date et d’heure utilisent la culture du thread actuelle pour les opérations de mise en forme. Pour spécifier explicitement que la méthode de mise en forme doit utiliser la culture actuelle, vous pouvez appeler une surcharge d’une méthode de mise en forme qui a un paramètre de fournisseur, comme [String.Format(IFormatProvider, String, Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) ou [DateTime.ToString(IFormatProvider)](xref:System.DateTime.ToString(System.IFormatProvider)), puis lui passer la propriété [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture). 

Vous pouvez rendre persistantes des données non-chaînées soit comme données binaires, soit comme données mises en forme. Si vous choisissez de l’enregistrer comme données mises en forme, vous devez appeler une surcharge de méthode de mise en forme qui inclut un paramètre *provider* et le passer à la propriété [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture). La culture dite indifférente fournit un format cohérent pour les données mises en forme qui est indépendant de la culture et de l'ordinateur. En revanche, assurer la persistance de données mises en forme à l'aide de cultures autres que la culture dite indifférente a plusieurs limites : 

* Les données seront vraisemblablement inutilisables si elles sont récupérées sur un système ayant une autre culture, ou si l'utilisateur du système actuel change la culture actuelle et essaie de récupérer les données. 

* Les propriétés d'une culture sur un ordinateur spécifique peuvent différer des valeurs standard. À tout moment, un utilisateur peut personnaliser les paramètres d'affichage selon la culture. De ce fait, les données mises en forme sont stockées sur un système et peuvent ne pas être lisibles lorsque l'utilisateur personnalise les paramètres de culture. La portabilité des données mises en forme sur différents ordinateurs peut être encore plus limitée. 

* Les normes internationales, régionales ou nationales qui régissent la mise en forme des nombres ou des dates et heures évoluent au fil du temps, et ces modifications sont intégrées dans les mises à jour du système d’exploitation. Quand les conventions de mise en forme changent, les données qui ont été mises en forme en utilisant les conventions antérieures peuvent devenir illisibles. 

L'exemple suivant illustre la portabilité limitée qui résulte de l'utilisation de la mise en forme qui tient compte de la culture pour assurer la persistance des données. L'exemple enregistre un tableau de valeurs de date et d'heure dans un fichier. Celles-ci sont mises en forme en utilisant les conventions culturelles de l'anglais (États-Unis). Une fois que l'application change la culture du thread actuel pour appliquer le français (Suisse), elle essaie de lire les valeurs enregistrées en utilisant les conventions de mise en forme de la culture actuelle. La tentative de lecture de deux des éléments de données lève une exception [FormatException](xref:System.FormatException) et le tableau de dates contient maintenant deux éléments incorrects égaux à [MinValue](xref:System.DateTime.MinValue). 

```csharp
using System;
using System.Globalization;
using System.IO;
using System.Text;
using System.Threading;

public class Example
{
   private static string filename = @".\dates.dat";

   public static void Main()
   {
      DateTime[] dates = { new DateTime(1758, 5, 6, 21, 26, 0), 
                           new DateTime(1818, 5, 5, 7, 19, 0), 
                           new DateTime(1870, 4, 22, 23, 54, 0),  
                           new DateTime(1890, 9, 8, 6, 47, 0), 
                           new DateTime(1905, 2, 18, 15, 12, 0) }; 
      // Write the data to a file using the current culture.
      WriteData(dates);
      // Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH");
      // Read the data using the current culture.
      DateTime[] newDates = ReadData();
      foreach (var newDate in newDates)
         Console.WriteLine(newDate.ToString("g"));
   }

   private static void WriteData(DateTime[] dates) 
   {
      StreamWriter sw = new StreamWriter(filename, false, Encoding.UTF8);    
      for (int ctr = 0; ctr < dates.Length; ctr++) {
         sw.Write("{0}", dates[ctr].ToString("g", CultureInfo.CurrentCulture));
         if (ctr < dates.Length - 1) sw.Write("|");   
      }      
      sw.Close();
   }

   private static DateTime[] ReadData() 
   {
      bool exceptionOccurred = false;

      // Read file contents as a single string, then split it.
      StreamReader sr = new StreamReader(filename, Encoding.UTF8);
      string output = sr.ReadToEnd();
      sr.Close();   

      string[] values = output.Split( new char[] { '|' } );
      DateTime[] newDates = new DateTime[values.Length]; 
      for (int ctr = 0; ctr < values.Length; ctr++) {
         try {
            newDates[ctr] = DateTime.Parse(values[ctr], CultureInfo.CurrentCulture);
         }
         catch (FormatException) {
            Console.WriteLine("Failed to parse {0}", values[ctr]);
            exceptionOccurred = true;
         }
      }      
      if (exceptionOccurred) Console.WriteLine();
      return newDates;
   }
}
// The example displays the following output:
//       Failed to parse 4/22/1870 11:54 PM
//       Failed to parse 2/18/1905 3:12 PM
//       
//       05.06.1758 21:26
//       05.05.1818 07:19
//       01.01.0001 00:00
//       09.08.1890 06:47
//       01.01.0001 00:00
//       01.01.0001 00:00
```

```vb
Imports System.Globalization
Imports System.IO
Imports System.Text
Imports System.Threading

Module Example
   Private filename As String = ".\dates.dat"

   Public Sub Main()
      Dim dates() As Date = { #5/6/1758 9:26PM#, #5/5/1818 7:19AM#, _ 
                              #4/22/1870 11:54PM#, #9/8/1890 6:47AM#, _ 
                              #2/18/1905 3:12PM# }
      ' Write the data to a file using the current culture.
      WriteData(dates)
      ' Change the current culture.
      Thread.CurrentThread.CurrentCulture = CultureInfo.CreateSpecificCulture("fr-CH")
      ' Read the data using the current culture.
      Dim newDates() As Date = ReadData()
      For Each newDate In newDates
         Console.WriteLine(newDate.ToString("g"))
      Next
   End Sub

   Private Sub WriteData(dates() As Date)
      Dim sw As New StreamWriter(filename, False, Encoding.Utf8)    
      For ctr As Integer = 0 To dates.Length - 1
         sw.Write("{0}", dates(ctr).ToString("g", CultureInfo.CurrentCulture))
         If ctr < dates.Length - 1 Then sw.Write("|")   
      Next      
      sw.Close()
   End Sub

   Private Function ReadData() As Date()
      Dim exceptionOccurred As Boolean = False

      ' Read file contents as a single string, then split it.
      Dim sr As New StreamReader(filename, Encoding.Utf8)
      Dim output As String = sr.ReadToEnd()
      sr.Close()   

      Dim values() As String = output.Split( {"|"c } )
      Dim newDates(values.Length - 1) As Date 
      For ctr As Integer = 0 To values.Length - 1
         Try
            newDates(ctr) = DateTime.Parse(values(ctr), CultureInfo.CurrentCulture)
         Catch e As FormatException
            Console.WriteLine("Failed to parse {0}", values(ctr))
            exceptionOccurred = True
         End Try
      Next      
      If exceptionOccurred Then Console.WriteLine()
      Return newDates
   End Function
End Module
' The example displays the following output:
'       Failed to parse 4/22/1870 11:54 PM
'       Failed to parse 2/18/1905 3:12 PM
'       
'       05.06.1758 21:26
'       05.05.1818 07:19
'       01.01.0001 00:00
'       09.08.1890 06:47
'       01.01.0001 00:00
'       01.01.0001 00:00
'
```

Toutefois, si vous remplacez la propriété [CultureInfo.CurrentCulture](xref:System.Globalization.CultureInfo.CurrentCulture) par [CultureInfo.InvariantCulture](xref:System.Globalization.CultureInfo.InvariantCulture) dans les appels à [DateTime.ToString(String, IFormatProvider)](xref:System.DateTime.ToString(System.String,System.IFormatProvider)) et [DateTime.Parse(String, IFormatProvider)](xref:System.DateTime.Parse(System.String,System.IFormatProvider)), les données de date et d’heure persistantes sont correctement restaurées, comme le montre la sortie suivante.

```
// 06.05.1758 21:26
// 05.05.1818 07:19
// 22.04.1870 23:54
// 08.09.1890 06:47
// 18.02.1905 15:12
```

## <a name="see-also"></a>Voir aussi

[Manipulation de chaînes](manipulating-strings.md)



<!--HONumber=Nov16_HO1-->


