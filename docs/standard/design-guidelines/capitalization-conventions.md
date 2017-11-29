---
title: Conventions de mise en majuscules
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1bddb7bb3559e6f39b7884b92f64bee8fbb3510
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="capitalization-conventions"></a>Conventions de mise en majuscules
Les instructions de cette mise en page chapitre une méthode simple pour l’utilisation de cas qui, en cas d’application constamment, assurez-vous des identificateurs pour les types, membres et paramètres faciles à lire.  
  
## <a name="capitalization-rules-for-identifiers"></a>Règles de casse des identificateurs  
 Afin de distinguer des mots dans un identificateur, pour mettre en majuscule la première lettre de chaque mot dans l’identificateur. N’utilisez pas de traits de soulignement pour différencier des mots, ou d’ailleurs, n’importe où dans les identificateurs. Il existe deux façons appropriés pour tirer profit des identificateurs, en fonction de l’utilisation de l’identificateur :  
  
-   Casse Pascal  
  
-   casse mixte  
  
 La convention de casse Pascal, utilisée pour tous les identificateurs à l’exception des noms de paramètres, met en majuscule le premier caractère de chaque mot (y compris les acronymes sur les deux lettres longueur), comme indiqué dans les exemples suivants :  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Un cas particulier concerne des acronymes de deux lettres correspondant à la fois des lettres sont en majuscules, comme indiqué dans l’identificateur suivant :  
  
 `IOStream`  
  
 La convention de casse mixte, utilisée uniquement pour les noms de paramètres, met en majuscule le premier caractère de chaque mot, sauf le premier mot, comme indiqué dans les exemples suivants. Comme dans l’exemple également, les acronymes de deux lettres qui commencent un identificateur à casse mixte sont en minuscules.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ FAIRE** utilisent la casse Pascal pour tous les noms de membre, le type et espace de noms publics constitué de plusieurs mots.  
  
 **✓ FAIRE** utilisez la casse mixte pour les noms de paramètre.  
  
 Le tableau suivant décrit les règles de mise en majuscules pour différents types d’identificateurs.  
  
|Identificateur|Casse|Exemple|  
|----------------|------------|-------------|  
|Espace de noms|Pascal|`namespace System.Security { ... }`|  
|Type|Pascal|`public class StreamReader { ... }`|  
|Interface|Pascal|`public interface IEnumerable { ... }`|  
|Méthode|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|  
|Propriété|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|  
|Événement|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|  
|Champ|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|  
|Valeur d’énumération|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|  
|Paramètre|Mixte|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Mise en majuscule de mots composés et les termes courants  
 La plupart des termes composés sont traités comme des mots isolés pour les besoins de mise en majuscules.  
  
 **X ne sont pas** majuscule chaque soi-disant fermé mots composés.  
  
 Il s’agit de mots composés écrits comme un mot unique, comme point de terminaison. Les instructions de la casse, à des fins de traiter un mot composé fermé comme un mot unique. Utiliser un dictionnaire actuel pour déterminer si un mot composé est écrit dans une forme fermée.  
  
|Pascal|Mixte|pas|  
|------------|-----------|---------|  
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
  
## <a name="case-sensitivity"></a>Respect de la casse  
 Les langues qui peuvent s’exécuter sur le CLR ne sont pas requis pour prendre en charge le respect de la casse, bien que certains. Même si votre langage prend en charge, autres langages qui peuvent accéder à votre version de framework ne le font pas. Des API qui sont accessibles de l’extérieur, par conséquent, ne peut pas vous fier cas seul pour faire la distinction entre les deux noms dans le même contexte.  
  
 **X ne sont pas** supposent que tous les langages de programmation respectent la casse. mais ils ne le sont pas. Les noms ne peuvent pas différer par la casse uniquement.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Affectation de noms](../../../docs/standard/design-guidelines/naming-guidelines.md)
