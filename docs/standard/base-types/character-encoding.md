---
title: "Encodage de caractères dans .NET"
description: "Encodage de caractères dans .NET"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bce54e41-e9dc-493a-8988-1cbadc340fe8
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: 6080f5fa12a2391dd138828e0afc2219f1e3a11b

---

# <a name="character-encoding-in-net"></a>Encodage de caractères dans .NET

Les caractères sont des entités abstraites qui peuvent être représentées de nombreuses façons différentes. Un encodage de caractères est un système qui associe chaque caractère d'un jeu de caractères pris en charge à une valeur qui représente ce caractère. Par exemple, le code Morse est un encodage de caractères qui associe chaque caractère de l'alphabet latin à une séquence de points et de tirets qui conviennent pour la transmission sur des lignes télégraphiques. Un encodage de caractères pour les ordinateurs associe chaque caractère d'un jeu de caractères à une valeur numérique qui représente ce caractère. Un encodage de caractères a deux composants distincts :

* Un encodeur, qui convertit une séquence de caractères en une séquence de valeurs numériques (octets).

* Un décodeur, qui convertit une séquence d'octets en une séquence de caractères.

L'encodage de caractères décrit les règles selon lesquelles un encodeur et un décodeur fonctionnent. Par exemple, la classe [UTF8Encoding](xref:System.Text.UTF8Encoding) décrit les règles d’encodage et de décodage UTF-8, qui utilise de un à quatre octets pour représenter un caractère Unicode. L’encodage et le décodage peuvent également inclure une validation. Par exemple, la classe [UnicodeEncoding](xref:System.Text.UnicodeEncoding) vérifie tous les substituts afin de vérifier qu’ils constituent des paires de substitution valide. (Une paire de substitution se compose d'un caractère avec un point de code allant de U+D800 à U+DBFF, suivi d'un caractère avec un point de code allant de U+DC00 à U+DFFF.) Une stratégie de secours détermine comment un encodeur traite les caractères non valides ou comment un décodeur gère les octets non valides. 

> [!WARNING]
> Les classes d’encodage .NET permettent de stocker et de convertir les données caractères. Elles ne doivent pas utilisées pour stocker des données binaires sous forme de chaîne. En fonction de l'encodage utilisé, la conversion de données binaires en un format chaîne avec les classes d'encodage peut entraîner un comportement inattendu et produire des données incorrectes ou endommagées. Pour convertir les données binaires en chaîne, utilisez la méthode [Convert.ToBase64String](xref:System.Convert.ToBase64String(System.Byte[])). 
 
.NET utilise l’encodage UTF-16 (représenté par la classe [UnicodeEncoding](xref:System.Text.UnicodeEncoding)) pour représenter des caractères et des chaînes. Les applications qui ciblent le common language runtime utilisent des encodeurs pour mapper les représentations de caractères Unicode prises en charge par le common language runtime à d'autres schémas de codage. Elles utilisent des décodeurs pour mapper les caractères des encodages non-Unicode à Unicode.

Cette rubrique contient les sections suivantes :

* [Encodages dans .NET](#encodings-in-net)

* [Sélection d’une classe d’encodage](#selecting-an-encoding-class)

* [Utilisation d’un objet d’encodage](#using-an-encoding-object)

* [Choix d’une stratégie de secours](#choosing-a-fallback-strategy)

* [Implémentation d’une stratégie de secours personnalisée](#implementing-a-custom-fallback-strategy)

## <a name="encodings-in-net"></a>Encodages dans .NET

Toutes les classes d’encodage de caractères dans .NET héritent de la classe [System.Text.Encoding](xref:System.Text.Encoding), qui est une classe abstraite définissant les fonctionnalités communes à tous les encodages de caractères. Pour accéder aux objets d’encodage individuels implémentés dans .NET, procédez comme suit :

* Utilisez les propriétés statiques de la classe [Encoding](xref:System.Text.Encoding), qui retournent des objets représentant les encodages de caractères standard disponibles dans .NET (ASCII, UTF-7, UTF-8, UTF-16 et UTF-32). Par exemple, la propriété [Encoding.Unicode](xref:System.Text.Encoding.Unicode) retourne un objet [UnicodeEncoding](xref:System.Text.UnicodeEncoding). Chaque objet utilise la stratégie de secours pour les remplacements pour traiter les chaînes qu'il ne peut pas encoder et les octets qu'il ne peut pas décoder. (Pour plus d’informations, consultez la section [Stratégie de secours pour les remplacements](#replacement-fallback).)

* Appelez le constructeur de classe de l'encodage. Les objets pour les encodages ASCII, UTF-7, UTF-8, UTF-16 et UTF-32 peuvent être instanciés de cette façon. Par défaut, chaque objet utilise la stratégie de secours pour les remplacements pour traiter les chaînes qu'il ne peut pas encoder et les octets qu'il ne peut pas décoder, mais vous pouvez spécifier qu'au lieu de cela, une exception doit être levée. (Pour plus d’informations, consultez les sections [Stratégie de secours pour les remplacements](#replacement-fallback) et [Stratégie de secours pour les exceptions](#exception-fallback).)

* Appelez le constructeur [Encoding.Encoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) et passez-lui un entier qui représente l’encodage. Les objets d'encodage standard utilisent la stratégie de secours pour les remplacements. Les objets d'encodage de page de codes et de jeu de caractères codés sur deux octets (DBCS) utilisent la stratégie de secours la mieux adaptée pour traiter les chaînes qu'ils ne peuvent pas encoder et les octets qu'ils ne peuvent pas décoder. (Pour plus d’informations, consultez la section [Stratégie de secours la mieux adaptée](#best-fit-fallback).)

* Appelez la méthode [Encoding.GetEncoding](xref:System.Text.Encoding.GetEncoding(System.Int32)), qui retourne les encodages standard, de page de codes ou DBCS disponibles dans .NET. Les surcharges vous permettent de spécifier un objet de secours pour l'encodeur et pour le décodeur.

> [!NOTE]
> La norme Unicode affecte un point de code (un nombre) et un nom à chaque caractère de chaque jeu de caractères pris en charge. Par exemple, le caractère "A" est représenté par le point de code U+0041 et par le nom "LETTRE MAJUSCULE LATINE A". Les encodages UTF (Unicode Transformation Format) définissent des moyens d'encoder ce point de code en une séquence d'un ou plusieurs octets. Un schéma d'encodage Unicode simplifie le développement d'applications mondialisées, car il permet la représentation avec un encodage unique des caractères provenant de n'importe quel jeu de caractères. Les développeurs d'applications ne doivent plus faire le suivi du schéma d'encodage qui a été utilisé pour produire des caractères pour une langue ou un système d'écriture spécifique, et les données peuvent être partagées entre des systèmes à une échelle internationale sans risque d'endommagement.
>
>  .NET prend en charge trois encodages définis par la norme Unicode : UTF-8, UTF-16 et UTF-32. Pour plus d’informations, consultez la norme Unicode dans la page d’accueil [Unicode](http://www.unicode.org/).
 
.NET prend en charge les systèmes d’encodage de caractères répertoriés dans le tableau suivant.

Encodage | Classe | Description | Avantages et inconvénients
-------- | ----- | ----------- | ------------------------ 
ASCII | [ASCIIEncoding](xref:System.Text.ASCIIEncoding) | Encode une plage de caractères limitée en utilisant les sept bits de poids le plus faible d'un octet. | Étant donné que cet encodage prend en charge seulement des valeurs de caractère de U+0000 à U+007F, dans la plupart des cas, il ne convient pas aux applications internationalisées.
UTF-7 | [UTF7Encoding](xref:System.Text.UTF7Encoding) | Représente les caractères sous forme de séquences de caractères ASCII sur 7 bits. Les caractères Unicode non-ASCII sont représentés par une séquence d'échappement de caractères ASCII. | UTF-7 prend en charge les protocoles de messagerie et les protocoles de groupe de discussion. UTF-7 n'est cependant pas particulièrement sécurisé ou robuste. Dans certains cas, la modification d'un seul bit peut changer radicalement l'interprétation de toute une chaîne UTF-7. Dans d'autres cas, des chaînes UTF-7 différentes peuvent correspondre à l'encodage d'un même texte. Pour les séquences incluant des caractères non-ASCII, UTF-7 nécessite davantage d'espace qu'UTF-8, et l'encodage/décodage est plus lent. Par conséquent, il est préférable d'utiliser UTF-8 au lieu d'UTF-7 si c'est possible.
UTF-8 | [UTF8Encoding](xref:System.Text.UTF8Encoding) | Représente chaque point de code Unicode sous la forme d'une séquence de un à quatre octets. | UTF-8 prend en charge des tailles de données de 8 bits et fonctionne bien avec de nombreux systèmes d'exploitation. Pour la plage de caractères ASCII, UTF-8 est identique à l'encodage ASCII et permet un ensemble de caractères plus large. Cependant, pour les jeux de caractères Chinois-Japonais-Coréen (CJC), UTF-8 peut nécessiter trois octets pour chaque caractère et aboutir potentiellement à des tailles de données supérieures à celles d'UTF-16. Notez que parfois, la quantité de données ASCII, comme des balises HTML, justifie l'augmentation de la taille pour les jeux de caractères CJC.
UTF-16 | [UnicodeEncoding](xref:System.Text.UnicodeEncoding) | Représente chaque point de code Unicode sous la forme d'une séquence de un ou deux entiers sur 16 bits. La plupart des caractères Unicode courants ne nécessitent qu'un seul point de code UTF-16, tandis que les caractères Unicode additionnels (U+10000 et supérieurs) nécessitent deux points de code de substitution UTF-16. Les ordres des octets Little Endian et Big Endian sont pris en charge. | L’encodage UTF-16 est utilisé par le Common Language Runtime pour représenter les valeurs Char et String, et il est utilisé par le système d’exploitation Windows pour représenter les valeurs WCHAR.
UTF-32 | [UTF32Encoding](xref:System.Text.UTF32Encoding) | Représente chaque point de code Unicode sous la forme d'un entier 32 bits. Les ordres des octets Little Endian et Big Endian sont pris en charge. | L'encodage UTF-32 est utilisé quand les applications ne doivent pas avoir le comportement du point de code de substitution de l'encodage UTF-16 sur les systèmes d'exploitation pour lesquels l'espace encodé est trop important. Les glyphes uniques restitués à l'affichage peuvent néanmoins encore être encodés avec plusieurs caractères UTF-32.

Ces encodages vous permettent de travailler avec des caractères Unicode ainsi qu'avec les encodages les plus couramment utilisés dans les applications héritées. En outre, vous pouvez créer un encodage personnalisé en définissant une classe qui dérive de [Encoding](xref:System.Text.Encoding) et en remplaçant ses membres.

> [!NOTE]
> Par défaut, .NET Core ne met à disposition aucune page de codes autre que la page de codes 28591 et les encodages Unicode, comme UTF-8 et UTF-16. Vous pouvez cependant ajouter à votre application les encodages des pages de code qui se trouvent dans les applications Windows standard ciblant le .NET Framework. Pour plus d’informations, consultez la rubrique [EncodingProvider](xref:System.Text.EncodingProvider). 

## <a name="selecting-an-encoding-class"></a>Sélection d’une classe d’encodage

Si vous avez la possibilité de choisir l’encodage utilisé par votre application, utilisez un encodage Unicode, de préférence [UTF8Encoding](xref:System.Text.UTF8Encoding) ou [UnicodeEncoding](xref:System.Text.UnicodeEncoding). (.NET prend également en charge un troisième encodage Unicode, [UTF32Encoding](xref:System.Text.UTF32Encoding).) 

Si vous envisagez d’utiliser un encodage ASCII ([ASCIIEncoding](xref:System.Text.ASCIIEncoding)), choisissez [UTF8Encoding](xref:System.Text.UTF8Encoding) à la place. Les deux encodages sont identiques pour le jeu de caractères ASCII, mais [UTF8Encoding](xref:System.Text.UTF8Encoding) présente les avantages suivants : 

* Il peut représenter tous les caractères Unicode, alors qu’[ASCIIEncoding](xref:System.Text.ASCIIEncoding) prend en charge seulement les valeurs des caractères Unicode comprises entre U+0000 et U+007F.

* Il offre une fonction de détection d'erreur et une meilleure sécurité.

* Il a été optimisé pour être aussi rapide que possible et il doit normalement être plus rapide n'importe quel autre encodage. Même pour du contenu qui est entièrement en ASCII, les opérations effectuées avec [UTF8Encoding](xref:System.Text.UTF8Encoding) sont plus rapides que les celles effectuées avec [ASCIIEncoding](xref:System.Text.ASCIIEncoding).

Il est préférable d’utiliser [ASCIIEncoding](xref:System.Text.ASCIIEncoding) seulement pour les applications héritées. Cependant, même pour les applications héritées, [UTF8Encoding](xref:System.Text.UTF8Encoding) peut être un meilleur choix pour les raisons suivantes (en supposant que les paramètres par défaut sont utilisés) :

* Si votre application a du contenu qui n’est pas strictement ASCII et qu’elle l’encode avec [ASCIIEncoding](xref:System.Text.ASCIIEncoding), chaque caractère non-ASCII est encodé sous la forme d’un point d’interrogation (?). Si l'application décode ensuite ces données, les informations sont perdues.


* Si votre application a du contenu qui n’est pas strictement ASCII et qu’elle l’encode avec [UTF8Encoding](xref:System.Text.UTF8Encoding), le résultat paraît inintelligible s’il est interprété comme étant en ASCII. Cependant, si l'application utilise ensuite un décodeur UTF-8 pour décoder ces données, les données apparaissent à nouveau correctes.

Dans une application web, les caractères envoyés au client en réponse à une demande web doivent refléter l'encodage utilisé sur le client. Dans la plupart des cas, vous devez affecter à la propriété [HttpResponse.ContentEncoding](xref:System.Net.HttpResponseHeader.ContentEncoding) la valeur retournée par la propriété [HttpRequestHeader.ContentEncoding](xref:System.Net.HttpRequestHeader.ContentEncoding) pour afficher le texte dans l’encodage attendu par l’utilisateur.

## <a name="using-an-encoding-object"></a>Utilisation d’un objet d’encodage

Un encodeur convertit une chaîne de caractères (le plus souvent, des caractères Unicode) en son équivalent numérique (en octets). Par exemple, vous pouvez utiliser un encodeur ASCII pour convertir des caractères Unicode en ASCII, pour pouvoir les afficher sur la console. Pour effectuer la conversion, vous appelez la méthode [Encoding.GetBytes](xref:System.Text.Encoding.GetBytes(System.Char[])). Pour déterminer le nombre d’octets nécessaires pour stocker les caractères encodés avant de procéder à l’encodage, vous pouvez appeler la méthode [GetByteCount](xref:System.Text.Encoding.GetByteCount(System.Char[])).

L'exemple suivant utilise un tableau d'octets seuls pour encoder des chaînes dans deux opérations distinctes. Il gère un index qui indique la position de départ dans le tableau d'octets pour l'ensemble suivant d'octets encodés en ASCII. Il appelle la méthode [ASCIIEncoding.GetByteCount(String)](xref:System.Text.ASCIIEncoding.GetByteCount(System.String)) pour vérifier que le tableau d’octets est assez grand pour contenir la chaîne encodée. Il appelle ensuite la méthode [ASCIIEncoding.GetBytes(String, Int32, Int32, Byte[], Int32)](xref:System.Text.ASCIIEncoding.GetBytes(System.Char[],System.Int32,System.Int32,System.Byte[],System.Int32)) pour encoder les caractères dans la chaîne.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings= { "This is the first sentence. ", 
                          "This is the second sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;

      // Create array of adequate size.
      byte[] bytes = new byte[49];
      // Create index for current position of array.
      int index = 0;

      Console.WriteLine("Strings to encode:");
      foreach (var stringValue in strings) {
         Console.WriteLine("   {0}", stringValue);

         int count = asciiEncoding.GetByteCount(stringValue);
         if (count + index >=  bytes.Length)
            Array.Resize(ref bytes, bytes.Length + 50);

         int written = asciiEncoding.GetBytes(stringValue, 0, 
                                              stringValue.Length, 
                                              bytes, index);    

         index = index + written; 
      } 
      Console.WriteLine("\nEncoded bytes:");
      Console.WriteLine("{0}", ShowByteValues(bytes, index));
      Console.WriteLine();

      // Decode Unicode byte array to a string.
      string newString = asciiEncoding.GetString(bytes, 0, index);
      Console.WriteLine("Decoded: {0}", newString);
   }

   private static string ShowByteValues(byte[] bytes, int last ) 
   {
      string returnString = "   ";
      for (int ctr = 0; ctr <= last - 1; ctr++) {
         if (ctr % 20 == 0)
            returnString += "\n   ";
         returnString += String.Format("{0:X2} ", bytes[ctr]);
      }
      return returnString;
   }
}
// The example displays the following output:
//       Strings to encode:
//          This is the first sentence.
//          This is the second sentence.
//       
//       Encoded bytes:
//       
//          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
//          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
//       
//       Decoded: This is the first sentence. This is the second sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII

      ' Create array of adequate size.
      Dim bytes(50) As Byte
      ' Create index for current position of array.
      Dim index As Integer = 0

      Console.WriteLine("Strings to encode:")
      For Each stringValue In strings
         Console.WriteLine("   {0}", stringValue)

         Dim count As Integer = asciiEncoding.GetByteCount(stringValue)
         If count + index >=  bytes.Length Then
            Array.Resize(bytes, bytes.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetBytes(stringValue, 0, 
                                                         stringValue.Length, 
                                                         bytes, index)    

         index = index + written 
      Next 
      Console.WriteLine()
      Console.WriteLine("Encoded bytes:")
      Console.WriteLine("{0}", ShowByteValues(bytes, index))
      Console.WriteLine()

      ' Decode Unicode byte array to a string.
      Dim newString As String = asciiEncoding.GetString(bytes, 0, index)
      Console.WriteLine("Decoded: {0}", newString)
   End Sub

   Private Function ShowByteValues(bytes As Byte(), last As Integer) As String
      Dim returnString As String = "   "
      For ctr As Integer = 0 To last - 1
         If ctr Mod 20 = 0 Then returnString += vbCrLf + "   "
         returnString += String.Format("{0:X2} ", bytes(ctr))
      Next
      Return returnString
   End Function
End Module
' The example displays the following output:
'       Strings to encode:
'          This is the first sentence.
'          This is the second sentence.
'       
'       Encoded bytes:
'       
'          54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'          6E 74 65 6E 63 65 2E 20 54 68 69 73 20 69 73 20 74 68 65 20
'          73 65 63 6F 6E 64 20 73 65 6E 74 65 6E 63 65 2E 20
'       
'       Decoded: This is the first sentence. This is the second sentence.
```

Un décodeur convertit un tableau d'octets qui reflète un encodage de caractères spécifique en un jeu de caractères dans un tableau de caractères ou dans une chaîne. Pour décoder un tableau d’octets en tableau de caractères, vous appelez la méthode [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])). Pour décoder un tableau d’octets en chaîne, vous appelez la méthode [GetString](xref:System.Text.Encoding.GetString(System.Byte[])). Pour déterminer le nombre d’octets nécessaires pour stocker les caractères décodés avant de procéder au décodage, vous pouvez appeler la méthode [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])).

L'exemple suivant encode trois chaînes, puis les décode dans un même tableau de caractères. Il gère un index qui indique la position de départ dans le tableau de caractères pour l'ensemble suivant de caractères décodés. Il appelle la méthode [GetCharCount](xref:System.Text.Encoding.GetCharCount(System.Byte[])) pour vérifier que le tableau de caractères est assez grand pour contenir les caractères décodés. Il appelle ensuite la méthode [ASCIIEncoding.GetChars(Byte[], Int32, Int32, Char[], Int32)](xref:System.Text.ASCIIEncoding.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) pour décoder le tableau d’octets.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      string[] strings = { "This is the first sentence. ", 
                           "This is the second sentence. ",
                           "This is the third sentence. " };
      Encoding asciiEncoding = Encoding.ASCII;
      // Array to hold encoded bytes.
      byte[] bytes;
      // Array to hold decoded characters.
      char[] chars = new char[50];
      // Create index for current position of character array.
      int index = 0;     

      foreach (var stringValue in strings) {
         Console.WriteLine("String to Encode: {0}", stringValue);
         // Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue);
         // Display the encoded bytes.
         Console.Write("Encoded bytes: ");
         for (int ctr = 0; ctr < bytes.Length; ctr++)
            Console.Write(" {0}{1:X2}", 
                          ctr % 20 == 0 ? Environment.NewLine : "", 
                          bytes[ctr]);
         Console.WriteLine();

         // Decode the bytes to a single character array.
         int count = asciiEncoding.GetCharCount(bytes);
         if (count + index >=  chars.Length)
            Array.Resize(ref chars, chars.Length + 50);

         int written = asciiEncoding.GetChars(bytes, 0, 
                                              bytes.Length, 
                                              chars, index);              
         index = index + written;
         Console.WriteLine();       
      }

      // Instantiate a single string containing the characters.
      string decodedString = new string(chars, 0, index - 1);
      Console.WriteLine("Decoded string: ");
      Console.WriteLine(decodedString);
   }
}
// The example displays the following output:
//    String to Encode: This is the first sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the second sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
//    65 6E 74 65 6E 63 65 2E 20
//    
//    String to Encode: This is the third sentence.
//    Encoded bytes:
//    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
//    6E 74 65 6E 63 65 2E 20
//    
//    Decoded string:
//    This is the first sentence. This is the second sentence. This is the third sentence.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim strings() As String = { "This is the first sentence. ", 
                                  "This is the second sentence. ",
                                  "This is the third sentence. " }
      Dim asciiEncoding As Encoding = Encoding.ASCII
      ' Array to hold encoded bytes.
      Dim bytes() As Byte
      ' Array to hold decoded characters.
      Dim chars(50) As Char
      ' Create index for current position of character array.
      Dim index As Integer     

      For Each stringValue In strings
         Console.WriteLine("String to Encode: {0}", stringValue)
         ' Encode the string to a byte array.
         bytes = asciiEncoding.GetBytes(stringValue)
         ' Display the encoded bytes.
         Console.Write("Encoded bytes: ")
         For ctr As Integer = 0 To bytes.Length - 1
            Console.Write(" {0}{1:X2}", If(ctr Mod 20 = 0, vbCrLf, ""), 
                                        bytes(ctr))
         Next         
         Console.WriteLine()

         ' Decode the bytes to a single character array.
         Dim count As Integer = asciiEncoding.GetCharCount(bytes)
         If count + index >=  chars.Length Then
            Array.Resize(chars, chars.Length + 50)
         End If
         Dim written As Integer = asciiEncoding.GetChars(bytes, 0, 
                                                         bytes.Length, 
                                                         chars, index)              
         index = index + written
         Console.WriteLine()       
      Next

      ' Instantiate a single string containing the characters.
      Dim decodedString As New String(chars, 0, index - 1)
      Console.WriteLine("Decoded string: ")
      Console.WriteLine(decodedString)
   End Sub
End Module
' The example displays the following output:
'    String to Encode: This is the first sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 66 69 72 73 74 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the second sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 73 65 63 6F 6E 64 20 73
'    65 6E 74 65 6E 63 65 2E 20
'    
'    String to Encode: This is the third sentence.
'    Encoded bytes:
'    54 68 69 73 20 69 73 20 74 68 65 20 74 68 69 72 64 20 73 65
'    6E 74 65 6E 63 65 2E 20
'    
'    Decoded string:
'    This is the first sentence. This is the second sentence. This is the third sentence.
```

Les méthodes d’encodage et de décodage d’une classe dérivée de [Encoding](xref:System.Text.Encoding) sont conçues pour fonctionner sur un ensemble de données complet ; autrement dit, toutes les données à encoder ou à décoder sont fournies dans un seul appel de méthode. Cependant, dans certains cas, les données sont disponibles dans un flux, et les données à encoder ou à décoder peuvent être disponibles seulement via des opérations de lecture distinctes. Ceci nécessite la conservation par l'opération d'encodage ou de décodage des états enregistrés depuis son précédent appel. Les méthodes des classes dérivées d’[Encoder](xref:System.Text.Encoder) et de [Decoder](xref:System.Text.Decoder) sont capables de traiter les opérations de codage et de décodage qui recouvrent plusieurs appels de méthode.

Un objet [Encoder](xref:System.Text.Encoder) est disponible pour un encodage particulier à partir de la propriété [Encoding.GetEncoder](xref:System.Text.Encoding.GetEncoder) de cet encodage. Un objet [Decoder](xref:System.Text.Decoder) est disponible pour un encodage particulier à partir de la propriété [Encoding.GetDecoder](xref:System.Text.Encoding.GetDecoder) de cet encodage. Pour les opérations de décodage, notez que les classes dérivées de [Decoder](xref:System.Text.Decoder) incluent une méthode [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)), mais qu’elles n’ont pas de méthode qui correspond à [Encoding.GetString](xref:System.Text.Encoding.GetString(System.Byte[])).

L’exemple suivant montre la différence entre l’utilisation des méthodes [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) et [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) pour le décodage d’un tableau d’octets Unicode. L'exemple encode une chaîne qui contient des caractères Unicode vers un fichier, puis utilise les deux méthodes de décodage pour les décoder par dix octets à la fois. Une paire de substitution se trouvant dans les dixième et onzième octets, elle est décodée dans des appels de méthode distincts. Comme la sortie le montre, la méthode [Encoding.GetChars](xref:System.Text.Encoding.GetChars(System.Byte[])) ne peut pas décoder correctement les octets et les remplace par U+FFFD (CARACTÈRE DE REMPLACEMENT). En revanche, la méthode [Decoder.GetChars](xref:System.Text.Decoder.GetChars(System.Byte[],System.Int32,System.Int32,System.Char[],System.Int32)) peut décoder correctement le tableau d’octets pour obtenir la chaîne d’origine.

```csharp
using System;
using System.IO;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Use default replacement fallback for invalid encoding.
      UnicodeEncoding enc = new UnicodeEncoding(true, false, false);

      // Define a string with various Unicode characters.
      string str1 = "AB YZ 19 \uD800\udc05 \u00e4"; 
      str1 += "Unicode characters. \u00a9 \u010C s \u0062\u0308"; 
      Console.WriteLine("Created original string...\n");

      // Convert string to byte array.                     
      byte[] bytes = enc.GetBytes(str1);

      FileStream fs = File.Create(@".\characters.bin");
      BinaryWriter bw = new BinaryWriter(fs);
      bw.Write(bytes);
      bw.Close();

      // Read bytes from file.
      FileStream fsIn = File.OpenRead(@".\characters.bin");
      BinaryReader br = new BinaryReader(fsIn);

      const int count = 10;            // Number of bytes to read at a time. 
      byte[] bytesRead = new byte[10]; // Buffer (byte array).
      int read;                        // Number of bytes actually read. 
      string str2 = String.Empty;      // Decoded string.

      // Try using Encoding object for all operations.
      do { 
         read = br.Read(bytesRead, 0, count);
         str2 += enc.GetString(bytesRead, 0, read); 
      } while (read == count);
      br.Close();
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...");
      CompareForEquality(str1, str2);
      Console.WriteLine();

      // Use Decoder for all operations.
      fsIn = File.OpenRead(@".\characters.bin");
      br = new BinaryReader(fsIn);
      Decoder decoder = enc.GetDecoder();
      char[] chars = new char[50];
      int index = 0;                   // Next character to write in array.
      int written = 0;                 // Number of chars written to array.
      do { 
         read = br.Read(bytesRead, 0, count);
         if (index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length) 
            Array.Resize(ref chars, chars.Length + 50);

         written = decoder.GetChars(bytesRead, 0, read, chars, index);
         index += written;                          
      } while (read == count);
      br.Close();            
      // Instantiate a string with the decoded characters.
      string str3 = new String(chars, 0, index); 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...");
      CompareForEquality(str1, str3); 
   }

   private static void CompareForEquality(string original, string decoded)
   {
      bool result = original.Equals(decoded);
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal));
      if (! result) {
         Console.WriteLine("Code points in original string:");
         foreach (var ch in original)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();

         Console.WriteLine("Code points in decoded string:");
         foreach (var ch in decoded)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
         Console.WriteLine();
      }
   }
}
// The example displays the following output:
//    Created original string...
//    
//    Decoded string using UnicodeEncoding.GetString()...
//    original = decoded: False
//    Code points in original string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    Code points in decoded string:
//    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
//    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
//    0020 0073 0020 0062 0308
//    
//    Decoded string using UnicodeEncoding.Decoder.GetString()...
//    original = decoded: True
```

```vb
Imports System.IO
Imports System.Text

Module Example
   Public Sub Main()
      ' Use default replacement fallback for invalid encoding.
      Dim enc As New UnicodeEncoding(True, False, False)

      ' Define a string with various Unicode characters.
      Dim str1 As String = String.Format("AB YZ 19 {0}{1} {2}", 
                                         ChrW(&hD800), ChrW(&hDC05), ChrW(&h00e4))
      str1 += String.Format("Unicode characters. {0} {1} s {2}{3}", 
                            ChrW(&h00a9), ChrW(&h010C), ChrW(&h0062), ChrW(&h0308))
      Console.WriteLine("Created original string...")
      Console.WriteLine()

      ' Convert string to byte array.                     
      Dim bytes() As Byte = enc.GetBytes(str1)

      Dim fs As FileStream = File.Create(".\characters.bin")
      Dim bw As New BinaryWriter(fs)
      bw.Write(bytes)
      bw.Close()

      ' Read bytes from file.
      Dim fsIn As FileStream = File.OpenRead(".\characters.bin")
      Dim br As New BinaryReader(fsIn)

      Const count As Integer = 10      ' Number of bytes to read at a time. 
      Dim bytesRead(9) As Byte         ' Buffer (byte array).
      Dim read As Integer              ' Number of bytes actually read. 
      Dim str2 As String = ""          ' Decoded string.

      ' Try using Encoding object for all operations.
      Do 
         read = br.Read(bytesRead, 0, count)
         str2 += enc.GetString(bytesRead, 0, read) 
      Loop While read = count
      br.Close()
      Console.WriteLine("Decoded string using UnicodeEncoding.GetString()...")
      CompareForEquality(str1, str2)
      Console.WriteLine()

      ' Use Decoder for all operations.
      fsIn = File.OpenRead(".\characters.bin")
      br = New BinaryReader(fsIn)
      Dim decoder As Decoder = enc.GetDecoder()
      Dim chars(50) As Char
      Dim index As Integer = 0         ' Next character to write in array.
      Dim written As Integer = 0       ' Number of chars written to array.
      Do 
         read = br.Read(bytesRead, 0, count)
         If index + decoder.GetCharCount(bytesRead, 0, read) - 1 >= chars.Length Then 
            Array.Resize(chars, chars.Length + 50)
         End If   
         written = decoder.GetChars(bytesRead, 0, read, chars, index)
         index += written                          
      Loop While read = count
      br.Close()            
      ' Instantiate a string with the decoded characters.
      Dim str3 As New String(chars, 0, index) 
      Console.WriteLine("Decoded string using UnicodeEncoding.Decoder.GetString()...")
      CompareForEquality(str1, str3) 
   End Sub

   Private Sub CompareForEquality(original As String, decoded As String)
      Dim result As Boolean = original.Equals(decoded)
      Console.WriteLine("original = decoded: {0}", 
                        original.Equals(decoded, StringComparison.Ordinal))
      If Not result Then
         Console.WriteLine("Code points in original string:")
         For Each ch In original
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()

         Console.WriteLine("Code points in decoded string:")
         For Each ch In decoded
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
' The example displays the following output:
'    Created original string...
'    
'    Decoded string using UnicodeEncoding.GetString()...
'    original = decoded: False
'    Code points in original string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 D800 DC05 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    Code points in decoded string:
'    0041 0042 0020 0059 005A 0020 0031 0039 0020 FFFD FFFD 0020 00E4 0055 006E 0069 0063 006F
'    0064 0065 0020 0063 0068 0061 0072 0061 0063 0074 0065 0072 0073 002E 0020 00A9 0020 010C
'    0020 0073 0020 0062 0308
'    
'    Decoded string using UnicodeEncoding.Decoder.GetString()...
'    original = decoded: True
```

## <a name="choosing-a-fallback-strategy"></a>Choix d’une stratégie de secours

Quand une méthode tente d'encoder ou de décoder un caractère, mais qu'il n'existe pas de mappage, elle doit implémenter une stratégie de secours qui détermine comment l'échec du mappage doit être traité. Il existe trois types de stratégies de secours : 

* Stratégie de secours la mieux adaptée

* Stratégie de secours pour les remplacements

* Stratégie de secours pour les exceptions

> [!IMPORTANT]
> Les problèmes les plus courants des opérations d'encodage se produisent quand un caractère Unicode ne peut pas être mappé à un encodage de page de codes particulier. Les problèmes les plus courants des opérations de décodage se produisent quand des séquences d'octets non valides ne peut pas être traduites en caractères Unicode valides. Pour ces raisons, vous devez savoir quelle stratégie de secours est utilisée par un objet de codage particulier. Chaque fois que c'est possible, vous devez spécifier la stratégie de secours utilisée par un objet d'encodage quand vous instanciez l'objet.
 
### <a name="bestfit-fallback"></a>Stratégie de secours la mieux adaptée

Quand un caractère n'a pas de correspondance exacte dans l'encodage cible, l'encodeur peut essayer de le mapper à un caractère similaire. (La stratégie de secours la mieux adaptée est principalement un codage plutôt qu'un problème de décodage. Il existe très peu de pages de codes contenant des caractères qui ne peuvent pas être mappés à Unicode.) La stratégie de secours la mieux adaptée correspond aux valeurs par défaut des encodages de pages de codes et de jeux de caractères codés sur deux octets, qui sont récupérés par les surcharges [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) et [Encoding.GetEncoding(String)](xref:System.Text.Encoding.GetEncoding(System.String)).

> [!NOTE]
> En théorie, les classes d’encodage Unicode fournies dans .NET ([UTF8Encoding](xref:System.Text.UTF8Encoding), [UnicodeEncoding](xref:System.Text.UnicodeEncoding) et [UTF32Encoding](xref:System.Text.UTF32Encoding)) prennent en charge tous les caractères de tous les jeux de caractères : elles peuvent donc être utilisées pour éliminer les problèmes liés à la stratégie de secours la mieux adaptée. 
 

Les stratégies de secours les mieux adaptées varient pour les différentes pages de code et elles ne sont pas documentées en détail. Par exemple, pour certaines pages de codes, les caractères latins à pleine chasse sont mappés aux caractères latins à demi-chasse plus courants. Pour d'autres pages de codes, ce mappage n'est pas effectué. Même avec une stratégie la plus adaptée appliquée de façon agressive, il n'existe pas d'ajustement possible pour certains caractères dans certains encodages. Par exemple, un idéogramme chinois n'a pas de mappage acceptable avec la page de codes 1252. Dans ce cas, une chaîne de remplacement est utilisée. Par défaut, cette chaîne est simplement un POINT D'INTERROGATION (U+003F).

L'exemple suivant utilise la page de codes 1252 (la page de codes Windows pour les langues d'Europe occidentale) pour illustrer le mappage le mieux adapté et ses inconvénients. La méthode [Encoding.GetEncoding(Int32)](xref:System.Text.Encoding.GetEncoding(System.Int32)) est utilisée pour récupérer un objet d’encodage pour la page de codes 1252. Par défaut, elle utilise un mappage le mieux adapté pour les caractères Unicode qu'elle ne prend pas en charge. L'exemple instancie une chaîne contenant trois caractères non-ASCII, LETTRE MAJUSCULE LATINE S CERCLÉE (U+24C8), EXPOSANT CINQ (U+2075) et INFINI (U+221E), séparés par des espaces. Comme le montre la sortie de l'exemple, quand la chaîne est encodée, les trois caractères d'origine autres qu'un espace sont remplacés par POINT D'INTERROGATION (U+003F), CHIFFRE CINQ (U+0035) et CHIFFRE HUIT (U+0038). CHIFFRE HUIT est un substitut particulièrement médiocre pour le caractère INFINI non pris en charge, et POINT D'INTERROGATION indique qu'aucun mappage n'est disponible pour le caractère d'origine.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      // Get an encoding for code page 1252 (Western Europe character set).
      Encoding cp1252 = Encoding.GetEncoding(1252);

      // Define and display a string.
      string str = "\u24c8 \u2075 \u221e";
      Console.WriteLine("Original string: " + str);
      Console.Write("Code points in string: ");
      foreach (var ch in str)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");   

      // Encode a Unicode string.
      Byte[] bytes = cp1252.GetBytes(str);
      Console.Write("Encoded bytes: ");
      foreach (byte byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the string.
      string str2 = cp1252.GetString(bytes);
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2));
      if (! str.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));
      }
   }
}
// The example displays the following output:
//       Original string: Ⓢ ⁵ ∞
//       Code points in string: 24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 35 20 38
//       
//       String round-tripped: False
//       ? 5 8
//       003F 0020 0035 0020 0038
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      ' Get an encoding for code page 1252 (Western Europe character set).
      Dim cp1252 As Encoding = Encoding.GetEncoding(1252)

      ' Define and display a string.
      Dim str As String = String.Format("{0} {1} {2}", ChrW(&h24c8), ChrW(&H2075), ChrW(&h221E))
      Console.WriteLine("Original string: " + str)
      Console.Write("Code points in string: ")
      For Each ch In str
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next
      Console.WriteLine()   
      Console.WriteLine()

      ' Encode a Unicode string.
      Dim bytes() As Byte = cp1252.GetBytes(str)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the string.
      Dim str2 As String = cp1252.GetString(bytes)
      Console.WriteLine("String round-tripped: {0}", str.Equals(str2))
      If Not str.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
      End If
   End Sub
End Module
' The example displays the following output:
'       Original string: Ⓢ ⁵ ∞
'       Code points in string: 24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 35 20 38
'       
'       String round-tripped: False
'       ? 5 8
'       003F 0020 0035 0020 0038
```

Le mappage le mieux adapté est le comportement par défaut d’un objet [Encoding](xref:System.Text.Encoding) qui encode des données Unicode en données de page de codes, et il existe des applications héritées qui s’appuient sur ce comportement. Cependant, la plupart des nouvelles applications doivent éviter ce comportement le mieux adapté pour des raisons de sécurité. Par exemple, les applications ne doivent pas établir un nom de domaine via un encodage le mieux adapté.

> [!Note]
> Vous pouvez également implémenter un mappage de stratégie de secours la mieux adaptée personnalisé pour un encodage. Pour plus d’informations, consultez la section [Implémentation d’une stratégie de secours personnalisée](#implementing-a-custom-fallback-strategy).
 
Si la stratégie de secours la mieux adaptée est la valeur par défaut d’un objet d’encodage, vous pouvez choisir une autre stratégie de secours quand vous récupérez un objet [Encoding](xref:System.Text.Encoding) en appelant la surcharge [Encoding.GetEncoding(Int32, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)) ou [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)). La section suivante contient un exemple qui remplace chaque caractère qui ne peut pas être mappé à la page de codes 1252 par un astérisque (\*).

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

### <a name="replacement-fallback"></a>Stratégie de secours pour les remplacements

Quand un caractère n'a pas de correspondance exacte dans le schéma cible, mais qu'il n'existe pas de caractère approprié auquel il peut être mappé, l'application peut spécifier un caractère ou une chaîne de remplacement. Il s'agit du comportement par défaut pour le décodeur Unicode, qui remplace toutes les séquences de deux octets qu'il ne peut pas décoder par CARACTÈRE_DE_REMPLACEMENT (U+FFFD). C’est également le comportement par défaut de la classe [ASCIIEncoding](xref:System.Text.ASCIIEncoding), qui remplace chaque caractère qu’elle ne peut pas encoder ou décoder par un point d’interrogation. L'exemple suivant illustre le remplacement de caractères pour la chaîne Unicode de l'exemple précédent. Comme le montre la sortie, chaque caractère qui ne peut pas être décodé en une valeur d'octet ASCII est remplacé par 0x3F, qui est le code ASCII pour un point d'interrogation.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.ASCII;

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);
      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Encoded bytes: 3F 20 3F 20 3F
//       
//       Round-trip: False
//       ? ? ?
//       003F 0020 003F 0020 003F
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.Ascii

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Encoded bytes: 3F 20 3F 20 3F
'       
'       Round-trip: False
'       ? ? ?
'       003F 0020 003F 0020 003F
```

.NET inclut les classes [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) et [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback), qui substituent une chaîne de remplacement si un caractère ne correspond pas exactement dans une opération d’encodage ou de décodage. Par défaut, cette chaîne de remplacement est un point d'interrogation, mais vous pouvez appeler une surcharge de constructeur de classe pour choisir une autre chaîne. En général, la chaîne de remplacement est un caractère unique, même si ce n’est pas obligatoire. L’exemple suivant change le comportement de l’encodeur de la page de codes 1252 en instanciant un objet [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) qui utilise un astérisque (\*) comme chaîne de remplacement.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding cp1252r = Encoding.GetEncoding(1252, 
                                  new EncoderReplacementFallback("*"),
                                  new DecoderReplacementFallback("*"));

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine();

      byte[] bytes = cp1252r.GetBytes(str1);
      string str2 = cp1252r.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      } 
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       Round-trip: False
//       * * *
//       002A 0020 002A 0020 002A
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim cp1252r As Encoding = Encoding.GetEncoding(1252, 
                                         New EncoderReplacementFallback("*"),
                                         New DecoderReplacementFallback("*"))

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()

      Dim bytes() As Byte = cp1252r.GetBytes(str1)
      Dim str2 As String = cp1252r.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next    
         Console.WriteLine()
      End If 
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       Round-trip: False
'       * * *
'       002A 0020 002A 0020 002A
```

> [!NOTE]
> Vous pouvez également implémenter une classe de remplacement pour un encodage. Pour plus d’informations, consultez la section [Implémentation d’une stratégie de secours personnalisée](#implementing-a-custom-fallback-strategy).
 
En plus du POINT D'INTERROGATION (U+003F), le CARACTÈRE DE REMPLACEMENT Unicode (U+FFFD) est couramment utilisé comme chaîne de remplacement, en particulier lors du décodage de séquences d'octets qui ne peuvent pas être converties en caractères Unicode. Vous êtes cependant libre de choisir n'importe quelle chaîne de remplacement, qui peut contenir plusieurs caractères.

### <a name="exception-fallback"></a>Stratégie de secours pour les exceptions

Au lieu de fournir une stratégie de secours la mieux adaptée ou une chaîne de remplacement, un encodeur peut lever une exception [EncoderFallbackException](xref:System.Text.EncoderFallbackException) s’il ne peut pas encoder un jeu de caractères, et un décodeur peut lever une exception [DecoderFallbackException](xref:System.Text.DecoderFallbackException) s’il ne peut pas décoder un tableau d’octets. Pour lever une exception dans les opérations d’encodage et de décodage, vous fournissez respectivement un objet [EncoderFallbackException](xref:System.Text.EncoderFallbackException) et un objet [DecoderFallbackException](xref:System.Text.DecoderFallbackException) à la méthode [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)). L’exemple suivant montre la stratégie de secours pour les exceptions avec la classe ASCIIEncoding.

```csharp
using System;
using System.Text;

public class Example
{
   public static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", 
                                          new EncoderExceptionFallback(), 
                                          new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      foreach (var ch in str1)
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

      Console.WriteLine("\n");

      // Encode the original string using the ASCII encoder.
      byte[] bytes = {};
      try {
         bytes = enc.GetBytes(str1);
         Console.Write("Encoded bytes: ");
         foreach (var byt in bytes)
            Console.Write("{0:X2} ", byt);

         Console.WriteLine();
      }
      catch (EncoderFallbackException e) {
         Console.Write("Exception: ");
         if (e.IsUnknownSurrogate())
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index);
         else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index);
         return;
      }
      Console.WriteLine();

      // Decode the ASCII bytes.
      try {
         string str2 = enc.GetString(bytes);
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
         if (! str1.Equals(str2)) {
            Console.WriteLine(str2);
            foreach (var ch in str2)
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

            Console.WriteLine();
         } 
      }
      catch (DecoderFallbackException e) {
         Console.Write("Unable to decode byte(s) ");
         foreach (byte unknown in e.BytesUnknown)
            Console.Write("0x{0:X2} ");

         Console.WriteLine("at index {0}", e.Index);
      }
   }
}
// The example displays the following output:
//       Ⓢ ⁵ ∞
//       24C8 0020 2075 0020 221E
//       
//       Exception: Unable to encode 0x24C8 at index 0.
```

```vb
Imports System.Text

Module Example
   Public Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", 
                                                 New EncoderExceptionFallback(), 
                                                 New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&h24C8), ChrW(&h2075), ChrW(&h221E))
      Console.WriteLine(str1)
      For Each ch In str1
         Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
      Next    
      Console.WriteLine()
      Console.WriteLine() 

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = {}
      Try
         bytes = enc.GetBytes(str1)
         Console.Write("Encoded bytes: ")
         For Each byt In bytes
            Console.Write("{0:X2} ", byt)
         Next
         Console.WriteLine()
      Catch e As EncoderFallbackException
         Console.Write("Exception: ")
         If e.IsUnknownSurrogate() Then
            Console.WriteLine("Unable to encode surrogate pair 0x{0:X4} 0x{1:X3} at index {2}.", 
                              Convert.ToUInt16(e.CharUnknownHigh), 
                              Convert.ToUInt16(e.CharUnknownLow), 
                              e.Index)
         Else
            Console.WriteLine("Unable to encode 0x{0:X4} at index {1}.", 
                              Convert.ToUInt16(e.CharUnknown), 
                              e.Index)
         End If                              
         Exit Sub
      End Try
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Try
         Dim str2 As String = enc.GetString(bytes)
         Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
         If Not str1.Equals(str2) Then
            Console.WriteLine(str2)
            For Each ch In str2
               Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
            Next    
            Console.WriteLine()
         End If 
      Catch e As DecoderFallbackException
         Console.Write("Unable to decode byte(s) ")
         For Each unknown As Byte In e.BytesUnknown
            Console.Write("0x{0:X2} ")
         Next
         Console.WriteLine("at index {0}", e.Index)
      End Try
   End Sub
End Module
' The example displays the following output:
'       Ⓢ ⁵ ∞
'       24C8 0020 2075 0020 221E
'       
'       Exception: Unable to encode 0x24C8 at index 0.
```

> [!NOTE]
> Vous pouvez également implémenter un gestionnaire d'exceptions personnalisé pour une opération d'encodage. Pour plus d’informations, consultez la section [Implémentation d’une stratégie de secours personnalisée](#implementing-a-custom-fallback-strategy).
 
Les objets [EncoderFallbackException](xref:System.Text.EncoderFallbackException) et [DecoderFallbackException](xref:System.Text.DecoderFallbackException) fournissent les informations suivantes sur la condition qui a provoqué l’exception : 

* L’objet [EncoderFallbackException](xref:System.Text.EncoderFallbackException) comprend une méthode [IsUnknownSurrogate](xref:System.Text.EncoderFallbackException.IsUnknownSurrogate), qui indique si le ou les caractères qui ne peuvent pas être encodés représentent une paire de substitution inconnue (auquel cas la méthode retourne `true`) ou un seul caractère inconnu (auquel cas la méthode retourne `false`). Les caractères de la paire de substitution sont disponibles à partir des propriétés [EncoderFallbackException.CharUnknownHigh](xref:System.Text.EncoderFallbackException.CharUnknownHigh) et [EncoderFallbackException.CharUnknownLow](xref:System.Text.EncoderFallbackException.CharUnknownLow). Le caractère unique inconnu est disponible à partir de la propriété [EncoderFallbackException.CharUnknown](xref:System.Text.EncoderFallbackException.CharUnknown). La propriété [EncoderFallbackException.Index](xref:System.Text.EncoderFallbackException.Index) indique la position dans la chaîne du premier caractère qui n’a pas pu être encodé.

* L’objet [DecoderFallbackException](xref:System.Text.DecoderFallbackException) inclut une propriété [BytesUnknown](xref:System.Text.DecoderFallbackException.BytesUnknown) qui retourne un tableau d’octets qui ne peut pas être décodé. La propriété [DecoderFallbackException.Index](xref:System.Text.DecoderFallbackException.Index) indique la position de départ des octets inconnus.

Bien que les objets [EncoderFallbackException](xref:System.Text.EncoderFallbackException) et [DecoderFallbackException](xref:System.Text.DecoderFallbackException) fournissent des informations de diagnostic adéquates sur l’exception, ils ne donnent pas accès à la mémoire tampon d’encodage ou de décodage. Par conséquent, ils ne permettent pas le remplacement ou la correction des données non valides dans la méthode d'encodage ou de décodage.

## <a name="implementing-a-custom-fallback-strategy"></a>Implémentation d’une stratégie de secours personnalisée

En plus du mappage le mieux adapté implémenté en interne par les pages de codes, .NET comprend les classes suivantes pour l’implémentation d’une stratégie de secours :

* Utilisez [EncoderReplacementFallback](xref:System.Text.EncoderReplacementFallback) et [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) pour remplacer des caractères dans des opérations d’encodage.

* Utilisez [DecoderReplacementFallback](xref:System.Text.DecoderReplacementFallback) et [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) pour remplacer des caractères dans des opérations de décodage.

* Utilisez [EncoderExceptionFallback](xref:System.Text.EncoderExceptionFallback) et [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) pour lever une exception [EncoderFallbackException](xref:System.Text.EncoderFallbackException) quand un caractère ne peut pas être encodé.

* Utilisez [DecoderExceptionFallback](xref:System.Text.DecoderExceptionFallback) et [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) pour lever une exception [DecoderFallbackException](xref:System.Text.DecoderFallbackException) quand un caractère ne peut pas être décodé.

En outre, vous pouvez implémenter une solution personnalisée qui utilise une stratégie de secours la mieux adaptée, une stratégie de secours pour les remplacements ou une stratégie de secours pour les exceptions, en procédant comme suit : 

1. Dérivez une classe d’[EncoderFallback](xref:System.Text.EncoderFallback) pour les opérations d’encodage et de [DecoderFallback](xref:System.Text.DecoderFallback) pour les opérations de décodage.

2. Dérivez une classe d’[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) pour les opérations d’encodage et de [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) pour les opérations de décodage.

3. Pour la stratégie de secours pour les exeptions, si les classes [EncoderFallbackException](xref:System.Text.EncoderFallbackException) et [DecoderFallbackException](xref:System.Text.DecoderFallbackException) ne répondent pas à vos besoins, dérivez une classe d’un objet d’exception comme [Exception](xref:System.Exception) ou [ArgumentException](xref:System.ArgumentException).

### <a name="deriving-from-encoderfallback-or-decoderfallback"></a>Dérivation depuis EncoderFallback ou DecoderFallback

Pour implémenter une solution de stratégie de secours personnalisée, vous devez créer une classe qui hérite d’[EncoderFallback](xref:System.Text.EncoderFallback) pour les opérations d’encodage, et de [DecoderFallback](xref:System.Text.DecoderFallback) pour les opérations de décodage. Les instances de ces classes sont passées à la méthode [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)) et servent d’intermédiaire entre la classe d’encodage et l’implémentation de la stratégie de secours.

Quand vous créez une solution de secours personnalisée pour un encodeur ou un décodeur, vous devez implémenter les membres suivants :

* La propriété [EncoderFallback.MaxCharCount](xref:System.Text.EncoderFallback.MaxCharCount) ou [DecoderFallback.MaxCharCount](xref:System.Text.DecoderFallback.MaxCharCount), qui retourne le nombre maximal possible de caractères que les stratégies de secours la mieux adaptée, pour les remplacements ou pour les exceptions peuvent retourner pour remplacer un caractère unique. Pour une stratégie de secours pour les exceptions personnalisée, sa valeur est zéro. 

* La méthode [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) ou [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) qui retourne votre implémentation [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) ou [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) personnalisée. La méthode est appelée par l'encodeur quand il rencontre le premier caractère qu'il est impossible d'encoder correctement, ou par le décodeur quand il rencontre le premier octet qu'il est impossible de décoder correctement.

### <a name="deriving-from-encoderfallbackbuffer-or-decoderfallbackbuffer"></a>Dérivation depuis EncoderFallbackBuffer ou DecoderFallbackBuffer

Pour implémenter une solution de stratégie de secours personnalisée, vous devez aussi créer une classe qui hérite d’[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) pour les opérations d’encodage, et de [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) pour les opérations de décodage. Les instances de ces classes sont retournées par la méthode `CreateFallbackBuffer` des classes [EncoderFallback](xref:System.Text.EncoderFallback) et [DecoderFallback](xref:System.Text.DecoderFallback). La méthode [EncoderFallback.CreateFallbackBuffer](xref:System.Text.EncoderFallback.CreateFallbackBuffer) est appelée par l’encodeur quand il rencontre le premier caractère qu’il ne peut pas encoder, et la méthode [DecoderFallback.CreateFallbackBuffer](xref:System.Text.DecoderFallback.CreateFallbackBuffer) est appelée par le décodeur quand il rencontre un ou plusieurs octets qu’il ne peut pas décoder. Les classes [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) et [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) fournissent l’implémentation de la stratégie de secours. Chaque instance représente une mémoire tampon qui contient les caractères de secours destinés à remplacer le caractère qui ne peut pas être encodé ou la séquence d'octets qui ne peut pas être décodée.

Quand vous créez une solution de secours personnalisée pour un encodeur ou un décodeur, vous devez implémenter les membres suivants :

* La méthode [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.%23ctor) ou [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)). [EncoderFallbackBuffer.Fallback](xref:System.Text.EncoderFallbackBuffer.Fallback(System.Char,System.Char,System.Int32)) est appelée par l’encodeur pour fournir à la mémoire tampon de la stratégie de secours des informations concernant le caractère qu’elle ne peut pas encoder. Étant donné que le caractère à encoder peut être une paire de substitution, cette méthode est surchargée. Le caractère à encoder et son index dans la chaîne sont passés à une surcharge. La demi-zone haute et la demi-zone basse, ainsi que son index dans la chaîne, sont passés à la deuxième surcharge. La méthode [DecoderFallbackBuffer.Fallback](xref:System.Text.DecoderFallbackBuffer.Fallback(System.Byte[],System.Int32)) est appelée par le décodeur pour fournir à la mémoire tampon de la stratégie de secours des informations sur les octets qu’elle ne peut pas décoder. Cette méthode reçoit un tableau d'octets qu'elle ne peut pas décoder, ainsi que l'index du premier octet. La méthode de secours doit retourner `true` si la mémoire tampon de secours peut fournir un ou plusieurs caractères les mieux adaptés ou de remplacement ; sinon, elle doit retourner `false`. Pour une stratégie de secours pour les exceptions, la méthode de secours doit lever une exception.

* La méthode [EncoderFallbackBuffer.GetNextChar](xref:System.Text.EncoderFallbackBuffer.GetNextChar) ou [DecoderFallbackBuffer.GetNextChar](xref:System.Text.DecoderFallbackBuffer.GetNextChar), qui est appelée à plusieurs reprises par l’encodeur ou le décodeur pour obtenir le caractère suivant de la mémoire tampon de la stratégie de secours. Quand tous les caractères de secours ont été retournés, la méthode doit retourner U+0000. 

* La propriété [EncoderFallbackBuffer.Remaining](xref:System.Text.EncoderFallbackBuffer.Remaining) ou [DecoderFallbackBuffer.Remaining](xref:System.Text.DecoderFallbackBuffer.Remaining), qui retourne le nombre de caractères restants dans la mémoire tampon de la stratégie de secours.

* La méthode [EncoderFallbackBuffer.MovePrevious](xref:System.Text.EncoderFallbackBuffer.MovePrevious) ou [DecoderFallbackBuffer.MovePrevious](xref:System.Text.DecoderFallbackBuffer.MovePrevious), qui déplace la position actuelle dans la mémoire tampon de la stratégie de secours vers le caractère précédent.

* La méthode [EncoderFallbackBuffer.Reset](xref:System.Text.EncoderFallbackBuffer.Reset) ou [DecoderFallbackBuffer.Reset](xref:System.Text.DecoderFallbackBuffer.Reset), qui réinitialise la mémoire tampon de la stratégie de secours.

Si l’implémentation de la stratégie de secours est une stratégie de secours la mieux adaptée ou pour les remplacements, les classes dérivées d’[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer) et [DecoderFallbackBuffer](xref:System.Text.DecoderFallbackBuffer) gèrent également deux champs d’instance privés : le nombre exact de caractères dans la mémoire tampon et l’index du caractère suivant dans la mémoire tampon à retourner.

### <a name="an-encoderfallback-example"></a>Exemple basé sur EncoderFallback

L’exemple précédent utilisait une stratégie de sauvegarde pour les remplacements pour remplacer les caractères Unicode qui ne correspondaient pas aux caractères ASCII par un astérisque (\*). L'exemple suivant utilise à la place une implémentation de stratégie de secours la mieux adaptée personnalisée pour fournir un meilleur mappage des caractères non-ASCII.

Le code suivant définit une classe nommée `CustomMapper` qui est dérivée d’[EncoderFallback](xref:System.Text.EncoderFallback) pour gérer le mappage le mieux adapté des caractères non-ASCII. Sa méthode `CreateFallbackBuffer` renvoie un objet `CustomMapperFallbackBuffer`, qui fournit l’implémentation [EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer). La classe `CustomMapper` utilise un objet [Dictionary&lt;TKey, TValue&gt;](xref:System.Collections.Generic.Dictionary%602) pour stocker les mappages des caractères Unicode non pris en charge (la valeur de la clé) et leurs caractères 8 bits correspondants (qui sont stockés dans deux octets consécutifs dans un entier 64 bits). Pour que ce mappage soit disponible pour la mémoire tampon de secours, l'instance de `CustomMapper` est passée comme paramètre au constructeur de classe `CustomMapperFallbackBuffer`. Comme le mappage le plus long est la chaîne "INF" pour le caractère Unicode U+221E, la propriété `MaxCharCount` retourne 3. 

```csharp
public class CustomMapper : EncoderFallback
{
   public string DefaultString;
   internal Dictionary<ushort, ulong> mapping;

   public CustomMapper() : this("*")
   {   
   }

   public CustomMapper(string defaultString)
   {
      this.DefaultString = defaultString;

      // Create table of mappings
      mapping = new Dictionary<ushort, ulong>();
      mapping.Add(0x24C8, 0x53);
      mapping.Add(0x2075, 0x35);
      mapping.Add(0x221E, 0x49004E0046);
   }

   public override EncoderFallbackBuffer CreateFallbackBuffer()
   {
      return new CustomMapperFallbackBuffer(this);
   }

   public override int MaxCharCount
   {
      get { return 3; }
   } 
}
```

```vb
Public Class CustomMapper : Inherits EncoderFallback
   Public DefaultString As String
   Friend mapping As Dictionary(Of UShort, ULong)

   Public Sub New()
      Me.New("?")
   End Sub

   Public Sub New(ByVal defaultString As String)
      Me.DefaultString = defaultString

      ' Create table of mappings
      mapping = New Dictionary(Of UShort, ULong)
      mapping.Add(&H24C8, &H53)
      mapping.Add(&H2075, &H35)
      mapping.Add(&H221E, &H49004E0046)
   End Sub

   Public Overrides Function CreateFallbackBuffer() As System.Text.EncoderFallbackBuffer
      Return New CustomMapperFallbackBuffer(Me)
   End Function

   Public Overrides ReadOnly Property MaxCharCount As Integer
      Get
         Return 3
      End Get
   End Property
End Class
```

Le code suivant définit la classe `CustomMapperFallbackBuffer`, qui est dérivée d’[EncoderFallbackBuffer](xref:System.Text.EncoderFallbackBuffer). Le dictionnaire qui contient les mappages les mieux adaptés et qui est défini dans l'instance de `CustomMapper` est disponible à partir de son constructeur de classe. Sa méthode `Fallback` retourne `true` si un des caractères Unicode que l'encodeur ASCII ne peut pas encoder est défini dans le dictionnaire de mappage ; sinon, elle retourne `false`. Pour chaque stratégie de secours, la variable privée `count` indique le nombre de caractères qui restent à retourner, et la variable privée `index` indique la position du caractère suivant à retourner dans la mémoire tampon de la chaîne, `charsToReturn`. 

```csharp
public class CustomMapperFallbackBuffer : EncoderFallbackBuffer
{
   int count = -1;                   // Number of characters to return
   int index = -1;                   // Index of character to return
   CustomMapper fb; 
   string charsToReturn; 

   public CustomMapperFallbackBuffer(CustomMapper fallback)
   {
      this.fb = fallback;
   }

   public override bool Fallback(char charUnknownHigh, char charUnknownLow, int index)
   {
      // Do not try to map surrogates to ASCII.
      return false;
   }

   public override bool Fallback(char charUnknown, int index)
   {
      // Return false if there are already characters to map.
      if (count >= 1) return false;

      // Determine number of characters to return.
      charsToReturn = String.Empty;

      ushort key = Convert.ToUInt16(charUnknown);
      if (fb.mapping.ContainsKey(key)) {
         byte[] bytes = BitConverter.GetBytes(fb.mapping[key]);
         int ctr = 0;
         foreach (var byt in bytes) {
            if (byt > 0) {
               ctr++;
               charsToReturn += (char) byt;
            }
         }
         count = ctr;
      }
      else {
         // Return default.
         charsToReturn = fb.DefaultString;
         count = 1;
      }
      this.index = charsToReturn.Length - 1;

      return true;
   }

   public override char GetNextChar()
   {
      // We'll return a character if possible, so subtract from the count of chars to return.
      count--;
      // If count is less than zero, we've returned all characters.
      if (count < 0) 
         return '\u0000';

      this.index--;
      return charsToReturn[this.index + 1];
   }

   public override bool MovePrevious()
   {
      // Original: if count >= -1 and pos >= 0
      if (count >= -1) {
         count++;
         return true;
      }
      else {
         return false;
      }
   }

   public override int Remaining 
   {
      get { return count < 0 ? 0 : count; }
   }

   public override void Reset()
   {
      count = -1;
      index = -1;
   }
}
```

```vb
Public Class CustomMapperFallbackBuffer : Inherits EncoderFallbackBuffer

   Dim count As Integer = -1        ' Number of characters to return
   Dim index As Integer = -1        ' Index of character to return
   Dim fb As CustomMapper
   Dim charsToReturn As String

   Public Sub New(ByVal fallback As CustomMapper)
      MyBase.New()
      Me.fb = fallback
   End Sub

   Public Overloads Overrides Function Fallback(ByVal charUnknownHigh As Char, ByVal charUnknownLow As Char, ByVal index As Integer) As Boolean
      ' Do not try to map surrogates to ASCII.
      Return False
   End Function

   Public Overloads Overrides Function Fallback(ByVal charUnknown As Char, ByVal index As Integer) As Boolean
      ' Return false if there are already characters to map.
      If count >= 1 Then Return False

      ' Determine number of characters to return.
      charsToReturn = String.Empty

      Dim key As UShort = Convert.ToUInt16(charUnknown)
      If fb.mapping.ContainsKey(key) Then
         Dim bytes() As Byte = BitConverter.GetBytes(fb.mapping.Item(key))
         Dim ctr As Integer
         For Each byt In bytes
            If byt > 0 Then
               ctr += 1
               charsToReturn += Chr(byt)
            End If
         Next
         count = ctr
      Else
         ' Return default.
         charsToReturn = fb.DefaultString
         count = 1
      End If
      Me.index = charsToReturn.Length - 1

      Return True
   End Function

   Public Overrides Function GetNextChar() As Char
      ' We'll return a character if possible, so subtract from the count of chars to return.
      count -= 1
      ' If count is less than zero, we've returned all characters.
      If count < 0 Then Return ChrW(0)

      Me.index -= 1
      Return charsToReturn(Me.index + 1)
   End Function

   Public Overrides Function MovePrevious() As Boolean
      ' Original: if count >= -1 and pos >= 0
      If count >= -1 Then
         count += 1
         Return True
      Else
         Return False
      End If
   End Function

   Public Overrides ReadOnly Property Remaining As Integer
      Get
         Return If(count < 0, 0, count)
      End Get
   End Property

   Public Overrides Sub Reset()
      count = -1
      index = -1
   End Sub
End Class
```

Le code suivant instancie ensuite l’objet `CustomMapper` et passe une instance de celui-ci à la méthode [Encoding.GetEncoding(String, EncoderFallback, DecoderFallback)](xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)). La sortie indique que l'implémentation de la stratégie de secours la mieux adaptée gère correctement les trois caractères non-ASCII de la chaîne d'origine.

```csharp
using System;
using System.Collections.Generic;
using System.Text;

class Program
{
   static void Main()
   {
      Encoding enc = Encoding.GetEncoding("us-ascii", new CustomMapper(), new DecoderExceptionFallback());

      string str1 = "\u24C8 \u2075 \u221E";
      Console.WriteLine(str1);
      for (int ctr = 0; ctr <= str1.Length - 1; ctr++) {
         Console.Write("{0} ", Convert.ToUInt16(str1[ctr]).ToString("X4"));
         if (ctr == str1.Length - 1) 
            Console.WriteLine();
      }
      Console.WriteLine();

      // Encode the original string using the ASCII encoder.
      byte[] bytes = enc.GetBytes(str1);
      Console.Write("Encoded bytes: ");
      foreach (var byt in bytes)
         Console.Write("{0:X2} ", byt);

      Console.WriteLine("\n");

      // Decode the ASCII bytes.
      string str2 = enc.GetString(bytes);
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2));
      if (! str1.Equals(str2)) {
         Console.WriteLine(str2);
         foreach (var ch in str2)
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"));

         Console.WriteLine();
      }
   }
}
```

```vb
Imports System.Text
Imports System.Collections.Generic

Module Module1

   Sub Main()
      Dim enc As Encoding = Encoding.GetEncoding("us-ascii", New CustomMapper(), New DecoderExceptionFallback())

      Dim str1 As String = String.Format("{0} {1} {2}", ChrW(&H24C8), ChrW(&H2075), ChrW(&H221E))
      Console.WriteLine(str1)
      For ctr As Integer = 0 To str1.Length - 1
         Console.Write("{0} ", Convert.ToUInt16(str1(ctr)).ToString("X4"))
         If ctr = str1.Length - 1 Then Console.WriteLine()
      Next
      Console.WriteLine()

      ' Encode the original string using the ASCII encoder.
      Dim bytes() As Byte = enc.GetBytes(str1)
      Console.Write("Encoded bytes: ")
      For Each byt In bytes
         Console.Write("{0:X2} ", byt)
      Next
      Console.WriteLine()
      Console.WriteLine()

      ' Decode the ASCII bytes.
      Dim str2 As String = enc.GetString(bytes)
      Console.WriteLine("Round-trip: {0}", str1.Equals(str2))
      If Not str1.Equals(str2) Then
         Console.WriteLine(str2)
         For Each ch In str2
            Console.Write("{0} ", Convert.ToUInt16(ch).ToString("X4"))
         Next
         Console.WriteLine()
      End If
   End Sub
End Module
```

## <a name="see-also"></a>Voir aussi

[System.Text.Encoder](xref:System.Text.Encoder)

[System.Text.EncoderFallback](xref:System.Text.EncoderFallback)

[System.Text.Decoder](xref:System.Text.Decoder)

[System.Text.DecoderFallback](xref:System.Text.DecoderFallback)

[System.Text.Encoding](xref:System.Text.Encoding)







<!--HONumber=Nov16_HO1-->


