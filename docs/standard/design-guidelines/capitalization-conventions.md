---
title: "Conventions de mise en majuscules | Microsoft Docs"
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
  - "noms à casse mixte (.NET Framework)"
  - "indications de conception de bibliothèques de classes (.NET Framework), mise en majuscules"
  - "Noms à casse Pascal (.NET Framework)"
  - "respect de la casse, les conventions de mise en majuscules"
  - "noms (.NET Framework), mise en majuscules"
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# Conventions de mise en majuscules
Les instructions de ce chapitre mise en page une méthode simple pour l’utilisation de cas, lorsqu’il est appliqué de manière cohérente, vérifiez les identificateurs pour les types, membres et paramètres faciles à lire.  
  
## Règles de casse des identificateurs  
 Pour différencier des mots dans un identificateur, mettre en majuscules la première lettre de chaque mot dans l’identificateur. N’utilisez pas de traits de soulignement pour différencier des mots, ou d’ailleurs, n’importe où dans les identificateurs. Il existe deux façons appropriés profit des identificateurs, en fonction de l’utilisation de l’identificateur :  
  
-   Casse Pascal  
  
-   casse mixte  
  
 La convention de casse Pascal, utilisée pour tous les identificateurs à l’exception des noms de paramètre, met en majuscule le premier caractère de chaque mot \(y compris les acronymes sur deux lettres en longueur\), comme indiqué dans les exemples suivants :  
  
 `PropertyDescriptor`   
 `HtmlTag`  
  
 Un cas particulier concerne des acronymes de deux lettres dans laquelle les lettres sont en majuscules, comme indiqué dans l’identificateur suivant :  
  
 `IOStream`  
  
 La convention de casse mixte, utilisée uniquement pour les noms de paramètre, met en majuscule le premier caractère de chaque mot, sauf le premier mot, comme indiqué dans les exemples suivants. Comme dans l’exemple également, les acronymes de deux lettres qui commencent un identificateur à casse mixte sont en minuscules.  
  
 `propertyDescriptor`   
 `ioStream`   
 `htmlTag`  
  
 **✓ faire** utilisent la casse Pascal pour tous les noms de membre, le type et espace de noms publics composés de plusieurs mots.  
  
 **✓ faire** utilisez la casse mixte pour les noms de paramètre.  
  
 Le tableau suivant décrit les règles de mise en majuscules pour différents types d’identificateurs.  
  
|Identificateur|Casse|Exemple|  
|--------------------|-----------|-------------|  
|Espace de noms|Pascal|`namespace System.Security { ... }`|  
|Type|Pascal|`public class StreamReader { ... }`|  
|Interface|Pascal|`public interface IEnumerable { ... }`|  
|Méthode|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Propriété|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Événement|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Champ|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Valeur d’énumération|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Paramètre|Casse mixte|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## Mots composés et les termes courants relatifs à la mise en majuscule  
 La plupart des termes composés sont traités comme des mots isolés dans le cadre de la mise en majuscules.  
  
 **X ne pas** majuscule chaque soi\-disant mots composés fermés.  
  
 Il s’agit de mots composés écrits comme un mot unique, comme le point de terminaison. Pour les besoins de règles de casse, traitez un mot composé fermé comme un mot unique. Utiliser un dictionnaire actuel pour déterminer si un mot composé est écrit dans le formulaire fermé.  
  
|Pascal|Casse mixte|Pas|  
|------------|-----------------|---------|  
|`BitFlag`|`bitFlag`|`Bitflag`|  
|`Callback`|`callback`|`CallBack`|  
|`Canceled`|`canceled`|`Cancelled`|  
|`DoNot`|`doNot`|`Don't`|  
|`Email`|`email`|`EMail`|  
|`Endpoint`|`endpoint`|`EndPoint`|  
|`FileName`|`fileName`|`Filename`|  
|`Gridline`|`gridline`|`GridLine`|  
|`Hashtable`|`hashtable`|`HashTable`|  
|`Id`|`id`|`ID`|  
|`Indexes`|`indexes`|`Indices`|  
|`LogOff`|`logOff`|`LogOut`|  
|`LogOn`|`logOn`|`LogIn`|  
|`Metadata`|`metadata`|`MetaData, metaData`|  
|`Multipanel`|`multipanel`|`MultiPanel`|  
|`Multiview`|`multiview`|`MultiView`|  
|`Namespace`|`namespace`|`NameSpace`|  
|`Ok`|`ok`|`OK`|  
|`Pi`|`pi`|`PI`|  
|`Placeholder`|`placeholder`|`PlaceHolder`|  
|`SignIn`|`signIn`|`SignOn`|  
|`SignOut`|`signOut`|`SignOff`|  
|`UserName`|`userName`|`Username`|  
|`WhiteSpace`|`whiteSpace`|`Whitespace`|  
|`Writable`|`writable`|`Writeable`|  
  
## Respect de la casse  
 Langages qui peuvent s’exécuter sur le CLR ne sont pas tenus de prendre en charge le respect de la casse, bien que certains. Même si votre langage prend en charge, autres langages qui peuvent accéder à votre infrastructure ne le faites pas. Par conséquent, d’API qui sont accessibles de l’extérieur, ne peut pas s’appuient sur incident seul pour faire la distinction entre deux noms dans le même contexte.  
  
 **X ne pas** supposer que tous les langages de programmation respectent la casse. Ils ne sont pas. Les noms ne peuvent pas différer par leur casse uniquement.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications concernant l'attribution d'un nom](../../../docs/standard/design-guidelines/naming-guidelines.md)