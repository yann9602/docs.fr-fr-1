---
title: "Surcharges d’op&#233;rateur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "opérateurs (.NET Framework), des surcharges"
  - "opérateurs surchargés de noms [.NET Framework]"
  - "règles de conception de membres, opérateurs"
  - "opérateurs surchargés"
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Surcharges d’op&#233;rateur
Les surcharges d’opérateur autorise les types de framework apparaissent comme si elles étaient des primitives de langage intégrées.  
  
 Bien qu’autorisées et utile dans certaines situations, les surcharges d’opérateur doivent être utilisés avec précaution. Il existe de nombreux cas dans l’opérateur surcharge a été détournée, telles que le démarrage de concepteurs d’utiliser des opérateurs pour les opérations qui doivent être des méthodes simples. Les instructions suivantes vous permettent de choisir quand et comment utiliser la surcharge d’opérateur.  
  
 **X éviter** définissant les surcharges d’opérateur, sauf dans les types qui semble comme des types primitifs \(intégrés\).  
  
 **✓ envisagez** définir des surcharges d’opérateur dans un type qui doit sembler comme un type primitif.  
  
 Par exemple, <xref:System.String?displayProperty=fullName> a `operator==` et `operator!=` définies.  
  
 **✓ faire** définir des surcharges d’opérateur dans les structures représentant des nombres \(tel que <xref:System.Decimal?displayProperty=fullName>\).  
  
 **X ne pas** être jolies lorsque vous définissez des surcharges d’opérateur.  
  
 Surcharge d’opérateur est utile dans les cas dans lesquels il est difficile d’identifier quel sera le résultat de l’opération. Par exemple, il est intéressant de pouvoir soustraire une <xref:System.DateTime> d’une autre `DateTime` et obtenir un <xref:System.TimeSpan>. Toutefois, il n’est pas approprié d’utiliser l’opérateur d’union logique pour les requêtes union de deux bases de données ou à utiliser l’opérateur de décalage pour écrire dans un flux.  
  
 **X ne pas** fournissent des surcharges, sauf si au moins un des opérandes est du type définissant la surcharge d’opérateur.  
  
 **✓ faire** surcharger les opérateurs de manière symétrique.  
  
 Par exemple, si vous surchargez le `operator==`, vous devez aussi surcharger le `operator!=`. De même, si vous surchargez le `operator<`, vous devez aussi surcharger le `operator>`, et ainsi de suite.  
  
 **✓ envisagez** en fournissant des méthodes avec des noms conviviaux qui correspondent à chaque opérateur surchargé.  
  
 De nombreux langages ne gèrent pas la surcharge d’opérateur. Pour cette raison, il est recommandé que les types qui surchargent les opérateurs incluent une méthode secondaire avec un nom spécifique à un domaine approprié qui fournit des fonctionnalités équivalentes.  
  
 Le tableau suivant contient une liste d’opérateurs et les noms de méthode convivial correspondant.  
  
|Symbole d’opérateur c\#|Nom des métadonnées|Nom convivial|  
|-----------------------------|-------------------------|-------------------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|`&#124;`|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|`&#124;&#124;`|`op_LogicalOr`|`Or`|  
|`=`|`op_Assign`|`Assign`|  
|`<<`|`op_LeftShift`|`LeftShift`|  
|`>>`|`op_RightShift`|`RightShift`|  
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|  
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|  
|`==`|`op_Equality`|`Equals`|  
|`!=`|`op_Inequality`|`Equals`|  
|`>`|`op_GreaterThan`|`CompareTo`|  
|`<`|`op_LessThan`|`CompareTo`|  
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|  
|`<=`|`op_LessThanOrEqual`|`CompareTo`|  
|`*=`|`op_MultiplicationAssignment`|`Multiply`|  
|`-=`|`op_SubtractionAssignment`|`Subtract`|  
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|  
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|  
|`%=`|`op_ModulusAssignment`|`Mod`|  
|`+=`|`op_AdditionAssignment`|`Add`|  
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|  
|`&#124;=`|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### La surcharge d’opérateur \=\=  
 La surcharge `operator ==` est beaucoup plus compliqué. La sémantique de l’opérateur doivent être compatibles avec plusieurs autres membres, tels que <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
### Conversion, opérateurs  
 Opérateurs de conversion sont des opérateurs unaires qui permettent la conversion d’un type à un autre. Les opérateurs doivent être définis comme des membres statiques sur l’opérande ou le type de retour. Il existe deux types d’opérateurs de conversion : implicites et explicites.  
  
 **X ne pas** fournir un opérateur de conversion si cette conversion n’est pas clairement attendue par les utilisateurs finaux.  
  
 **X ne pas** définir des opérateurs de conversion en dehors du domaine d’un type.  
  
 Par exemple, <xref:System.Int32>, <xref:System.Double>, et <xref:System.Decimal> sont tous les types numériques, tandis que <xref:System.DateTime> n’est pas. Par conséquent, il ne doit y avoir aucun opérateur de conversion pour convertir un `Double(long)` à un `DateTime`. Dans ce cas, un constructeur est préféré.  
  
 **X ne pas** fournissent un opérateur de conversion implicite si la conversion est potentiellement avec perte de données.  
  
 Par exemple, ne doit contenir une conversion implicite de `Double` à `Int32` car `Double` a une plage plus étendue que `Int32`. Un opérateur de conversion explicite peut être fourni, même si la conversion est potentiellement avec perte de données.  
  
 **X ne pas** lever des exceptions de casts implicites.  
  
 Il est très difficile pour les utilisateurs finaux à comprendre ce qui se passe, car ils peuvent ne pas être conscient qu’une conversion est en cours.  
  
 **✓ faire** lever <xref:System.InvalidCastException?displayProperty=fullName> Si un appel à un opérateur de cast entraîne une conversion avec perte de données et le contrat de l’opérateur n’autorise pas de telles conversions.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Règles de conception de membres](../../../docs/standard/design-guidelines/member.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)