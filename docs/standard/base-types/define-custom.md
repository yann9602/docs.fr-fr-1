---
title: "Guide pratique : définir et utiliser des fournisseurs de format numérique personnalisés"
description: "Guide pratique pour définir et utiliser des fournisseurs de format numérique personnalisés"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 9b184114-6612-4c1a-a2db-2e24e65b0f77
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 926195e48e9653525a502cf9403ae9c205bd0fe3

---

# <a name="how-to-define-and-use-custom-numeric-format-providers"></a>Guide pratique : définir et utiliser des fournisseurs de format numérique personnalisés

.NET vous donne un contrôle étendu sur la représentation sous forme de chaîne de valeurs numériques. Il prend en charge les fonctionnalités suivantes pour personnaliser le format des valeurs numériques :

* Chaînes de format numériques standard, qui fournissent un ensemble prédéfini de formats pour convertir des nombres dans leur représentation sous forme de chaîne. Vous pouvez les utiliser avec toute méthode de mise en forme numérique, telle que [Decimal.ToString(String](xref:System.Decimal.ToString(System.String)), dotée d’un paramètre de format. Pour plus d’informations, consultez [Chaînes de format numériques standard](standard-numeric.md).

* Chaînes de format numériques personnalisées, qui fournissent un ensemble de symboles pouvant être combinés pour définir des spécificateurs de format numériques personnalisés. Elles peuvent également être utilisées avec toute méthode de mise en forme numérique, telle que [Decimal.ToString(String](xref:System.Decimal.ToString(System.String)), dotée d’un paramètre de format. Pour plus d’informations, consultez [Chaînes de format numériques personnalisées](custom-numeric.md).

* Objets [CultureInfo](xref:System.Globalization.CultureInfo) ou [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) personnalisés, qui définissent les symboles et les modèles de format utilisés pour afficher les représentations sous forme de chaîne des valeurs numériques. Vous pouvez les utiliser avec toute méthode de mise en forme numérique, telle que [ToString](xref:System.Int32.ToString(System.IFormatProvider)), dotée d’un paramètre de *fournisseur*. En règle générale, le paramètre de *fournisseur* est utilisé pour spécifier la mise en forme propre à la culture.

Dans certains cas (par exemple, quand une application doit afficher un numéro de compte mis en forme, un numéro d’identification ou un code postal), ces trois techniques sont inappropriées. .NET vous permet également de définir un objet de mise en forme qui n’est ni un objet [CultureInfo](xref:System.Globalization.CultureInfo) ni un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) pour déterminer la mise en forme d’une valeur numérique. Cette rubrique fournit des instructions détaillées pour l’implémentation de ce type d’objet et fournit un exemple qui met en forme les numéros de téléphone.

## <a name="to-define-a-custom-format-provider"></a>Pour définir un fournisseur de format personnalisé

1. Définissez une classe qui implémente les interfaces [IFormatProvider](xref:System.IFormatProvider) et [ICustomFormatter](xref:System.ICustomFormatter). 

2. Implémentez la méthode [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)). [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) est une méthode de rappel que la méthode de mise en forme (telle que la méthode [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object))) appelle pour récupérer l’objet qui est réellement chargé d’effectuer la mise en forme personnalisée. Une implémentation classique de [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) effectue les opérations suivantes :

    a. Elle détermine si l’objet [Type](xref:System.Type) passé comme paramètre de méthode représente une interface [ICustomFormatter](xref:System.ICustomFormatter).
    
    b. Si le paramètre représente l’interface [ICustomFormatter](xref:System.ICustomFormatter), [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retourne un objet qui implémente l’interface [ICustomFormatter](xref:System.ICustomFormatter) chargée de fournir la mise en forme personnalisée. En général, l’objet de mise en forme personnalisée retourne lui-même. 
    
    c. Si le paramètre ne représente pas l’interface [ICustomFormatter](xref:System.ICustomFormatter), [GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) retourne `null`.
    
3. Implémentez la méthode [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)). Cette méthode est appelée par la méthode [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)) et est chargée de retourner la représentation sous forme de chaîne d’un nombre. En général, l’implémentation de la méthode implique les étapes suivantes :

    a. Le cas échéant, vérifiez que la méthode est légitimement destinée à fournir des services de mise en forme en examinant le paramètre de *fournisseur*. Pour les objets de mise en forme qui implémentent à la fois [IFormatProvider](xref:System.IFormatProvider) et [ICustomFormatter](xref:System.ICustomFormatter), vous devez déterminer si le paramètre de *fournisseur* correspond à l’objet de mise en forme actuel.
    
    b. Déterminez si l’objet de mise en forme doit prendre en charge les spécificateurs de format personnalisés. (Par exemple, un spécificateur de format « N » peut indiquer qu’un numéro de téléphone américain doit être au format NANP, tandis qu’un spécificateur de format « I » peut indiquer une sortie au format ITU-T Recommandation E.123.) Si des spécificateurs de format sont utilisés, la méthode doit gérer le spécificateur de format spécifique. Il est passé à la méthode dans le paramètre de format. Si aucun spécificateur n’est présent, la valeur du paramètre *format* est [String.Empty](xref:System.String#System_String_Empty).
    
    c. Récupérez la valeur numérique passée à la méthode comme paramètre *arg*. Effectuez toute opération requise pour le convertir en sa représentation sous forme de chaîne.
    
    d. Retournez la représentation sous forme de chaîne du paramètre *arg*.
    
## <a name="to-use-a-custom-numeric-formatting-object"></a>Pour utiliser un objet de mise en forme numérique personnalisé

1. Créez une instance de la classe de mise en forme personnalisée.

2. Appelez la méthode de mise en forme [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)), en lui passant l’objet de mise en forme personnalisée, le spécificateur de mise en forme (ou [String.Empty](xref:System.String.Empty), si aucun n’est utilisé) et la valeur numérique à mettre en forme. 

## <a name="example"></a>Exemple

L’exemple suivant définit un fournisseur de format numérique personnalisé nommé `TelephoneFormatter` qui convertit un nombre représentant un numéro de téléphone aux États-Unis au format NANP ou E.123 correspondant. La méthode gère deux spécificateurs de format, « N » (qui génère le format NANP) et « I » (qui génère le format E.123 international).

```csharp
using System;
using System.Globalization;

public class TelephoneFormatter : IFormatProvider, ICustomFormatter
{
   public object GetFormat(Type formatType)
   {
      if (formatType == typeof(ICustomFormatter))
         return this;
      else
         return null;
   }               

   public string Format(string format, object arg, IFormatProvider formatProvider)
   {
      // Check whether this is an appropriate callback             
      if (! this.Equals(formatProvider))
         return null; 

      // Set default format specifier             
      if (string.IsNullOrEmpty(format)) 
         format = "N";

      string numericString = arg.ToString();

      if (format == "N")
      {
         if (numericString.Length <= 4)
            return numericString;
         else if (numericString.Length == 7)
            return numericString.Substring(0, 3) + "-" + numericString.Substring(3, 4); 
         else if (numericString.Length == 10)
               return "(" + numericString.Substring(0, 3) + ") " +
                      numericString.Substring(3, 3) + "-" + numericString.Substring(6);   
         else
            throw new FormatException( 
                      string.Format("'{0}' cannot be used to format {1}.", 
                                    format, arg.ToString()));
      }
      else if (format == "I")
      {
         if (numericString.Length < 10)
            throw new FormatException(string.Format("{0} does not have 10 digits.", arg.ToString()));
         else
            numericString = "+1 " + numericString.Substring(0, 3) + " " + numericString.Substring(3, 3) + " " + numericString.Substring(6);
      }
      else
      {
         throw new FormatException(string.Format("The {0} format specifier is invalid.", format));
      } 
      return numericString;  
   }
}

public class TestTelephoneFormatter
{
   public static void Main()
   {
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 0));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 911));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 8490216));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 4257884748));

      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 0));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 911));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 8490216));
      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 4257884748));

      Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:I}", 4257884748));
   }
}
```

```vb
Public Class TelephoneFormatter : Implements IFormatProvider, ICustomFormatter
   Public Function GetFormat(formatType As Type) As Object _
                   Implements IFormatProvider.GetFormat
      If formatType Is GetType(ICustomFormatter) Then
         Return Me
      Else
         Return Nothing
      End If               
   End Function               

   Public Function Format(fmt As String, arg As Object, _
                          formatProvider As IFormatProvider) As String _
                   Implements ICustomFormatter.Format
      ' Check whether this is an appropriate callback             
      If Not Me.Equals(formatProvider) Then Return Nothing 

      ' Set default format specifier             
      If String.IsNullOrEmpty(fmt) Then fmt = "N"

      Dim numericString As String = arg.ToString

      If fmt = "N" Then
         Select Case numericString.Length
            Case <= 4 
               Return numericString
            Case 7
               Return Left(numericString, 3) & "-" & Mid(numericString, 4) 
            Case 10
               Return "(" & Left(numericString, 3) & ") " & _
                      Mid(numericString, 4, 3) & "-" & Mid(numericString, 7)   
            Case Else
               Throw New FormatException( _
                         String.Format("'{0}' cannot be used to format {1}.", _
                                       fmt, arg.ToString()))
         End Select
      ElseIf fmt = "I" Then
         If numericString.Length < 10 Then
            Throw New FormatException(String.Format("{0} does not have 10 digits.", arg.ToString()))
         Else
            numericString = "+1 " & Left(numericString, 3) & " " & Mid(numericString, 4, 3) & " " & Mid(numericString, 7)
         End If      
      Else
         Throw New FormatException(String.Format("The {0} format specifier is invalid.", fmt))
      End If 
      Return numericString  
   End Function
End Class

Public Module TestTelephoneFormatter
   Public Sub Main
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 0))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 911))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 8490216))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 4257884748))

      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 0))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 911))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 8490216))
      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 4257884748))

      Console.WriteLine(String.Format(New TelephoneFormatter, "{0:I}", 4257884748))
   End Sub
End Module
```

Le fournisseur de format numérique personnalisé ne peut être utilisé qu’avec la méthode [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). Les autres surcharges des méthodes de mise en forme numérique (telles que `ToString`) dotées d’un paramètre de type [IFormatProvider](xref:System.IFormatProvider) passent toutes à l’implémentation [IFormatProvider.GetFormat](xref:System.IFormatProvider.GetFormat(System.Type)) un objet [Type](xref:System.Type) qui représente le type [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo). La méthode doit normalement leur retourner un objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo). Si elle ne le fait pas, le fournisseur de format numérique personnalisé est ignoré et l’objet [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) pour la culture actuelle est utilisé à la place. Dans l’exemple, la méthode `TelephoneFormatter.GetFormat` vérifie si la transmission à une méthode de mise en forme numérique est effectuée de façon inappropriée ; elle examine le paramètre de méthode et, si le type représenté n’est pas [ICustomFormatter](xref:System.ICustomFormatter), retourne une valeur *null*.

Si un fournisseur de format numérique personnalisé prend en charge un jeu de spécificateurs de format, vérifiez que vous fournissez un comportement par défaut si aucun spécificateur de format n’est fourni dans l’élément de format utilisé dans l’appel de la méthode [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). Dans l’exemple, « N » est le spécificateur de format par défaut. Cela permet de convertir un nombre en un numéro de téléphone mis en forme en fournissant un spécificateur de format explicite. L’exemple suivant illustre un appel de méthode de ce type.

```csharp
Console.WriteLine(String.Format(new TelephoneFormatter(), "{0:N}", 4257884748));
```

```vb
Console.WriteLine(String.Format(New TelephoneFormatter, "{0:N}", 4257884748))
```

Mais il permet également la conversion si aucun spécificateur de format n’est présent. L’exemple suivant illustre un appel de méthode de ce type.

```csharp
Console.WriteLine(String.Format(new TelephoneFormatter(), "{0}", 4257884748));
```

```vb
Console.WriteLine(String.Format(New TelephoneFormatter, "{0}", 4257884748))
```

Si aucun spécificateur de format par défaut n’est défini, votre implémentation de la méthode [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) doit inclure le code suivant afin que .NET puisse fournir la mise en forme que votre code ne prend pas en charge.

```csharp
if (arg is IFormattable) 
   s = ((IFormattable)arg).ToString(format, formatProvider);
else if (arg != null)    
   s = arg.ToString();
```

```vb
If TypeOf(arg) Is IFormattable Then 
   s = DirectCast(arg, IFormattable).ToString(fmt, formatProvider)
ElseIf arg IsNot Nothing Then    
   s = arg.ToString()
End If
```

Dans le cas de cet exemple, la méthode qui implémente [ICustomFormatter.Format](xref:System.ICustomFormatter.Format(System.String,System.Object,System.IFormatProvider)) est conçue pour servir de méthode de rappel pour la méthode [String.Format(IFormatProvider,String,Object[])](xref:System.String.Format(System.IFormatProvider,System.String,System.Object)). Ainsi, elle examine le paramètre *formatProvider* pour déterminer s’il contient une référence à l’objet `TelephoneFormatter`. Toutefois, la méthode peut également être appelée directement à partir du code. Dans ce cas, vous pouvez utiliser le paramètre *formatProvider* pour fournir un objet [CultureInfo](xref:System.Globalization.CultureInfo) ou [NumberFormatInfo](xref:System.Globalization.NumberFormatInfo) qui fournit des informations de mise en forme spécifiques à la culture.

## <a name="see-also"></a>Voir aussi

[Exécution d’opérations de mise en forme](performing-formatting-operations.md)



<!--HONumber=Nov16_HO1-->


