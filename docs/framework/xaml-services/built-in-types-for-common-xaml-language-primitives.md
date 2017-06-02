---
title: "Built-in Types for Common XAML Language Primitives | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XAML language primitives [XAML Services]"
  - "XAML [XAML Services], built-in types"
  - "x:String [XAML Services]"
  - "x:TimeSpan [XAML Services]"
  - "x:Byte [XAML Services]"
  - "x:Double [XAML Services]"
  - "XAML [XAML Services], types"
  - "x:Uri [XAML Services]"
  - "XAML built-in types [XAML Services]"
  - "x:Int64 [XAML Services]"
  - "x:Single [XAML Services]"
  - "x:Int32 [XAML Services]"
ms.assetid: 11de2f08-5b95-4989-b5ec-5178eb968184
caps.latest.revision: 11
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 11
---
# Built-in Types for Common XAML Language Primitives
XAML 2009 introduit la prise en charge de niveau de langage XAML pour plusieurs types de données qui sont des primitives fréquemment utilisées dans le Common Language Runtime \(CLR\) et dans d'autres langages de programmation. XAML 2009 ajoute la prise en charge des primitives suivantes : `x:Object`, `x:Boolean`, `x:Char`, `x:String`, `x:Decimal`, `x:Single`, `x:Double`, `x:Int16`, `x:Int32`, `x:Int64`, `x:TimeSpan`, `x:Uri`, `x:Byte` et `x:Array`  
  
<a name="previous_techniques_for_language_primitives_in_xaml_markup"></a>   
## Techniques précédentes pour les primitives du langage dans le balisage XAML  
 En XAML, pour les versions précédentes de WPF, vous pouviez faire référence aux primitives du langage CLR en mappant l'assembly et l'espace de noms qui contenaient une classe de définition de primitive CLR pour le .NET Framework. La plupart d'entre elles se trouvent dans l'assembly mscorlib et dans l'espace de noms <xref:System>. Par exemple, pour utiliser <xref:System.Int32>, vous pouviez déclarer le mappage suivant \(avec un exemple d'utilisation indiqué ensuite\) :  
  
```  
<Application xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml" xmlns:sys="clr-namespace:System;assembly=mscorlib"> <Application.Resources> <sys:Int32 x:Key="intMeaning">42</sys:Int32> </Application.Resources> </Application>  
```  
  
<a name="xaml_2009_language_primitives"></a>   
## Primitives de langage XAML 2009  
 Par convention, les primitives de langage pour XAML et tous les autres éléments de langage XAML sont affichés, notamment le préfixe `x:`. C'est ainsi que les éléments de langage XAML sont généralement utilisés dans le balisage réel. Cette convention est suivie de la documentation conceptuelle pour XAML dans WPF, ainsi que dans la spécification XAML.  
  
### x:Object  
 Pour le stockage CLR, la primitive `x:Object` correspond à <xref:System.Object>.  
  
 Cette primitive n'est généralement pas utilisée dans le balisage d'application, mais elle peut être utile pour certains scénarios tels que la vérification de l'assignabilité dans un système de type XAML.  
  
### x:Boolean  
 Pour le stockage CLR, la primitive `x:Boolean` correspond à <xref:System.Boolean>.  
  
 XAML analyse les valeurs de `x:Boolean` sans respect de la casse. Notez que `x:Bool` n'est pas une alternative acceptée. Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.17 et 5.4.11](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:Char  
 Pour le stockage CLR, la primitive `x:Char` correspond à <xref:System.Char>.  
  
 Les types de chaîne et de caractère ont une interaction avec l'encodage global du fichier au niveau XML. Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.7 et 5.4.1](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:String  
 Pour le stockage CLR, la primitive `x:String` correspond à <xref:System.String>.  
  
 Les types de chaîne et de caractère ont une interaction avec l'encodage global du fichier au niveau XML. Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:Decimal  
 Pour le stockage CLR, la primitive `x:Decimal` correspond à <xref:System.Decimal>.  
  
 Notez que l'analyse XAML est effectuée fondamentalement par rapport à la culture `en-US`. Dans la culture `en-US`, le séparateur approprié pour les composants d'une valeur décimale est toujours le point \(`.`\), indépendamment des paramètres de culture de l'environnement de développement, ou de la cible cliente éventuelle où le code XAML est chargé au moment de l'exécution.  
  
 Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.14 et 5.4.8](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:Single  
 Pour le stockage CLR, la primitive `x:Single` correspond à <xref:System.Single>.  
  
 Outre les valeurs numériques, la syntaxe de texte de `x:Single` autorise également les jetons `Infinity`, `-Infinity` et `NaN`. Ces jetons sont traités avec respect de la casse.  
  
 `x:Single` peut prendre en charge les valeurs sous forme de notation scientifique, si le premier caractère dans la syntaxe de texte est `e` ou `E`.  
  
 Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.8 et 5.4.2](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:Double  
 Pour le stockage CLR, la primitive `x:Double` correspond à <xref:System.Double>.  
  
 Outre les valeurs numériques, la syntaxe de texte de `x:Double` autorise les jetons `Infinity`, `-Infinity` et `NaN`. Ces jetons sont traités avec respect de la casse.  
  
 `x:Double` peut prendre en charge les valeurs sous forme de notation scientifique. Utilisez le caractère `e` ou `E` pour introduire la partie exposant.  
  
 Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.9 et 5.4.3](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:Int16  
 Pour le stockage CLR, la primitive `x:Int16` correspond à <xref:System.Int16> et `x:Int16` est considérée comme signée. En XAML, l'absence d'un signe plus \(`+`\) dans la syntaxe de texte indique implicitement une valeur signée positive.  
  
 Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.11 et 5.4.5](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:Int32  
 Pour le stockage CLR, la primitive `x:Int32` correspond à <xref:System.Int32>.`x:Int32` est considérée comme signée. En XAML, l'absence d'un signe plus \(`+`\) dans la syntaxe de texte indique implicitement une valeur signée positive.  
  
 Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.12 et 5.4.6](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:Int64  
 Pour le stockage CLR, la primitive `x:Int64` correspond à <xref:System.Int64>.`x:Int64` est considérée comme signée. En XAML, l'absence d'un signe plus \(`+`\) dans la syntaxe de texte indique implicitement une valeur signée positive.  
  
 Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.13 et 5.4.7](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:TimeSpan  
 Pour le stockage CLR, la primitive `x:TimeSpan` correspond à <xref:System.TimeSpan>.  
  
 Notez que l'analyse XAML pour le format heure\-date est effectuée fondamentalement par rapport à la culture `en-US`.  
  
 Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.16 et 5.4.10](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:Uri  
 Pour le stockage CLR, la primitive `x:Uri` correspond à <xref:System.Uri>.  
  
 La vérification des protocoles ne fait pas partie de la définition XAML de `x:Uri`.  
  
 Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.15 et 5.4.9](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:Byte  
 Pour le stockage CLR, la primitive `x:Byte` correspond à <xref:System.Byte>. Une primitive <xref:System.Byte> \/ `x:Byte` est considérée comme non signée.  
  
 Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.10 et 5.4.4](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
### x:Array  
 Pour le stockage CLR, la primitive `x:Array` correspond à <xref:System.Array>.  
  
 Vous pouvez définir un tableau dans XAML 2006 à l'aide d'une syntaxe d'extension de balisage ; toutefois, la syntaxe XAML 2009 est une primitive définie par le langage qui ne requiert pas l'accès à une extension de balisage. Pour plus d’informations sur la prise en charge de XAML 2006, consultez [x:Array Markup Extension](../../../docs/framework/xaml-services/x-array-markup-extension.md).  
  
 Pour connaître la définition de la spécification du langage XAML, consultez [\[MS\-XAML\] Sections 5.2.18](http://go.microsoft.com/fwlink/?LinkId=114525).  
  
<a name="wpf_support"></a>   
## Prise en charge de WPF  
 Dans WPF, vous pouvez utiliser les fonctionnalités XAML 2009, mais uniquement pour le code XAML qui n'est pas compilé par balisage. Le code XAML compilé par balisage pour WPF et la forme BAML du code XAML ne prennent actuellement pas en charge les mots clés et les fonctionnalités XAML 2009.  
  
 La création de code XAML libre, suivie du chargement de ce code XAML dans une exécution de WPF et dans un graphique d'objets avec <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=fullName> constitue un scénario dans lequel vous pouvez utiliser les fonctionnalités XAML 2009 avec WPF. La classe <xref:System.Windows.Markup.XamlReader?displayProperty=fullName> WPF et sa méthode <xref:System.Windows.Markup.XamlReader.Load%2A> peuvent traiter les mots clés de langage et fonctionnalités XAML 2009 dans une représentation de graphique d'objets valide.