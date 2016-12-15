---
title: "Fonctions math&#233;matiques (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "fonctions mathématiques, Visual Basic"
  - "opérations arithmétiques, fonctions mathématiques"
  - "routines mathématiques"
  - "Atn, fonction"
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Fonctions math&#233;matiques (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les méthodes de classe d' <xref:System.Math?displayProperty=fullName> fournissent fonctions mathématiques trigonométriques, logarithmiques, et autres courantes.  
  
## Notes  
 Le tableau suivant répertorie les méthodes de classe d' <xref:System.Math?displayProperty=fullName> .  Vous pouvez utiliser ces derniers dans un programme Visual Basic.  
  
|Méthode .NET Framework|Description|  
|----------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|Retourne la valeur absolue d'un nombre.|  
|<xref:System.Math.Acos%2A>|Retourne l'angle dont le cosinus est le nombre spécifié.|  
|<xref:System.Math.Asin%2A>|Retourne l'angle dont le sinus est le nombre spécifié.|  
|<xref:System.Math.Atan%2A>|Retourne l'angle dont la tangente est le nombre spécifié.|  
|<xref:System.Math.Atan2%2A>|Retourne l'angle dont la tangente est le quotient de deux nombres spécifiés.|  
|<xref:System.Math.BigMul%2A>|Retourne la version complète de deux nombres de 32 bits.|  
|<xref:System.Math.Ceiling%2A>|Retourne la plus petite valeur intégrale qui est supérieur ou égal à `Decimal` spécifié ou `Double`.|  
|<xref:System.Math.Cos%2A>|Retourne le cosinus de l'angle spécifié.|  
|<xref:System.Math.Cosh%2A>|Retourne le cosinus hyperbolique de l'angle spécifié.|  
|<xref:System.Math.DivRem%2A>|Retourne le quotient de deux de 32 bits ou d'entiers signés 64 bits, et retourne également le reste dans un paramètre de sortie.|  
|<xref:System.Math.Exp%2A>|Retourne e \(la base des logarithmes népériens\) déclenché à la puissance spécifiée.|  
|<xref:System.Math.Floor%2A>|Retourne le plus grand entier qui est inférieure ou égale à `Decimal` ou le nombre spécifié d' `Double` .|  
|<xref:System.Math.IEEERemainder%2A>|Retourne le reste qui est le résultat de la division d'un nombre spécifié par un autre nombre spécifié.|  
|<xref:System.Math.Log%2A>|Retourne le logarithme naturel \( ede base\) d'un nombre spécifié ou le logarithme d'un nombre spécifié dans une base spécifiée.|  
|<xref:System.Math.Log10%2A>|Retourne le logarithme de base 10 d'un nombre spécifié.|  
|<xref:System.Math.Max%2A>|Retourne le plus grand de deux nombres.|  
|<xref:System.Math.Min%2A>|Retourne le plus petit de deux nombres.|  
|<xref:System.Math.Pow%2A>|Retourne un nombre spécifié élevé à la puissance spécifiée.|  
|<xref:System.Math.Round%2A>|Retourne une valeur d' `Decimal` ou d' `Double` arrondie à la valeur intégrale la plus proche ou à un nombre de chiffres fractionnaires.|  
|<xref:System.Math.Sign%2A>|Retourne une valeur `Integer` indiquant le signe d'un nombre.|  
|<xref:System.Math.Sin%2A>|Retourne le sinus de l'angle spécifié.|  
|<xref:System.Math.Sinh%2A>|Retourne le sinus hyperbolique de l'angle spécifié.|  
|<xref:System.Math.Sqrt%2A>|Retourne la racine carrée d'un nombre spécifié.|  
|<xref:System.Math.Tan%2A>|Retourne la tangente de l'angle spécifié.|  
|<xref:System.Math.Tanh%2A>|Retourne la tangente hyperbolique de l'angle spécifié.|  
|<xref:System.Math.Truncate%2A>|Calcule la partie intégrante d' `Decimal` ou d'un nombre spécifié d' `Double` .|  
  
 Pour utiliser ces fonctions sans qualification, importez l'espace de noms d' <xref:System.Math?displayProperty=fullName> dans votre projet en ajoutant le code suivant en haut de votre fichier source :  
  
```  
Imports System.Math  
```  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Math.Abs%2A> de la classe <xref:System.Math> pour calculer la valeur absolue d'un nombre.  
  
```  
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Math.Atan%2A> de la classe <xref:System.Math> pour calculer la valeur de pi.  
  
```  
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Math.Cos%2A> de la classe <xref:System.Math> pour retourner le cosinus d'un angle.  
  
```  
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Math.Exp%2A> de la classe <xref:System.Math> pour retourner e élevé à une puissance.  
  
```  
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Math.Log%2A> de la classe <xref:System.Math> pour retourner le logarithme népérien d'un nombre.  
  
```  
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Math.Round%2A> de la classe <xref:System.Math> pour arrondir un nombre au nombre entier le plus proche.  
  
```  
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Math.Sign%2A> de la classe <xref:System.Math> pour déterminer le signe d'un nombre.  
  
```  
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Math.Sin%2A> de la classe <xref:System.Math> pour retourner le sinus d'un angle.  
  
```  
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Math.Sqrt%2A> de la classe <xref:System.Math> pour calculer la racine carrée d'un nombre.  
  
```  
' Returns 2.  
Dim MySqr1 As Double = Math.Sqrt(4)  
' Returns 4.79583152331272.  
Dim MySqr2 As Double = Math.Sqrt(23)  
' Returns 0.  
Dim MySqr3 As Double = Math.Sqrt(0)  
' Returns NaN (not a number).  
Dim MySqr4 As Double = Math.Sqrt(-4)  
```  
  
## Exemple  
 Cet exemple utilise la méthode <xref:System.Math.Tan%2A> de la classe <xref:System.Math> pour retourner la tangente d'un angle.  
  
```  
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## Configuration requise  
 **Classe :** <xref:System.Math>  
  
 **Espace de noms :** <xref:System>  
  
 **Assembly :** mscorlib \(dans mscorlib.dll\)  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>   
 <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>   
 <xref:System.Double.NaN>   
 [Derived Math Functions](../../../visual-basic/language-reference/keywords/derived-math-functions.md)   
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)