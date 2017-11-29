---
title: "Conventions générales d'affectation de noms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dde3adbb7640978829dea4b977ed14eec38a9077
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="general-naming-conventions"></a>Conventions générales d'affectation de noms
Cette section décrit d’affectation de noms conventions générales relatives au choix des mots, des recommandations sur l’utilisation des abréviations et les acronymes et les recommandations sur la façon d’éviter l’utilisation de noms spécifiques au langage.  
  
## <a name="word-choice"></a>Choix des mots  
 **✓ FAIRE** choisir des noms d’identificateurs lisibles.  
  
 Par exemple, une propriété nommée `HorizontalAlignment` est plus anglais-lisible que `AlignmentHorizontal`.  
  
 **✓ FAIRE** privilégier la lisibilité des raisons de concision.  
  
 Le nom de propriété `CanScrollHorizontally` est meilleure que `ScrollableX` (une référence à l’axe x).  
  
 **X ne sont pas** utiliser d’autres caractères non alphanumériques, des traits d’union ou des traits de soulignement.  
  
 **X ne sont pas** utilisent une notation hongroise.  
  
 **X Évitez** à l’aide d’identificateurs qui entrent en conflit avec les mots clés de largement utilisé des langages de programmation.  
  
 En fonction de la règle 4 du Common Language Specification (CLS), tous les langages conformes doivent fournir un mécanisme qui permet d’accéder à des éléments nommés qui utilisent un mot clé de cette langue en tant qu’identificateur. En c#, par exemple, utilise le signe comme un mécanisme d’échappement dans ce cas @. Toutefois, il est toujours conseillé d’éviter les mots clés courants, car il est beaucoup plus difficile d’utiliser une méthode avec la séquence d’échappement à l’autre sans.  
  
## <a name="using-abbreviations-and-acronyms"></a>À l’aide des acronymes et les abréviations  
 **X ne sont pas** utiliser des abréviations ou contractions comme faisant partie des noms d’identificateur.  
  
 Par exemple, utilisez `GetWindow` plutôt que `GetWin`.  
  
 **X ne sont pas** utiliser des acronymes ne sont pas largement reconnue et même si elles sont uniquement lorsque cela est nécessaire.  
  
## <a name="avoiding-language-specific-names"></a>Éviter des noms spécifiques au langage  
 **✓ FAIRE** utiliser des noms sémantiquement intéressants plutôt que des mots clés spécifiques à la langue pour les noms de type.  
  
 Par exemple, `GetLength` est un nom plus approprié que `GetInt`.  
  
 **✓ FAIRE** utiliser un nom de type CLR générique, plutôt que d’un nom spécifique au langage, dans les rares cas où un identificateur n’a aucune signification sémantique au-delà de son type.  
  
 Par exemple, une méthode de conversion en <xref:System.Int64> doivent être nommés `ToInt64`, et non `ToLong` (car <xref:System.Int64> est un nom CLR pour c#-alias spécifique `long`). Le tableau suivant présente plusieurs types de base de données utilisant les noms de types CLR (ainsi que les noms de types correspondants pour c#, Visual Basic et C++).  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Byte**|**unsigned char**|**Byte**|  
|**short**|**short**|**short**|**Int16**|  
|**ushort**|**UInt16**|**unsigned short**|**UInt16**|  
|**int**|**Integer**|**int**|**Int32**|  
|**uint**|**UInt32**|**unsigned int**|**UInt32**|  
|**long**|**Long**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|**unsigned __int64**|**UInt64**|  
|**float**|**Single**|**float**|**Single**|  
|**double**|**Double**|**double**|**Double**|  
|**bool**|**Boolean**|**bool**|**Boolean**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**string**|**String**|**String**|**String**|  
|**object**|**Objet**|**Objet**|**Objet**|  
  
 **✓ FAIRE** utiliser un nom commun, tel que `value` ou `item`, plutôt que de répéter le nom de type dans les rares cas où un identificateur n’a aucune signification sémantique et le type du paramètre n’est pas important.  
  
## <a name="naming-new-versions-of-existing-apis"></a>D’affectation de noms de nouvelles Versions d’API existantes  
 **✓ FAIRE** utiliser un nom semblable à l’ancien API lors de la création de nouvelles versions d’une API existante.  
  
 Cela permet de mettre en évidence la relation entre les API.  
  
 **✓ FAIRE** préférez l’ajout d’un suffixe au lieu d’un préfixe pour indiquer une nouvelle version d’une API existante.  
  
 Cela est utile pour la détection lorsque vous parcourez la documentation, ou à l’aide d’Intellisense. L’ancienne version de l’API est organisée proches les nouvelles API, car la plupart des navigateurs et Intellisense affichent les identificateurs dans l’ordre alphabétique.  
  
 **✓ Envisagez** à l’aide d’un identificateur de tout nouveau, mais significatif, au lieu d’ajouter un préfixe ou un suffixe.  
  
 **✓ FAIRE** un suffixe numérique permet d’indiquer une nouvelle version d’une API existante, en particulier si le nom existant de l’API est le seul nom logique (par exemple, si elle est une norme sectorielle) et si l’ajout explicite tout suffixe (ou la modification du nom) n’est pas une application option de ropriate.  
  
 **X ne sont pas** utiliser le « Ex » (ou un texte similaire) suffixe pour un identificateur pour le distinguer d’une version antérieure de la même API.  
  
 **✓ FAIRE** utiliser le suffixe « 64 » lorsque vous introduisez des versions d’API qui fonctionnent sur un entier 64 bits (un entier long) au lieu d’un entier 32 bits. Vous pouvez suivre cette approche lorsqu’il existe de l’API 32 bits existante ; ne le faites pour toute nouvelle API avec uniquement une version 64 bits.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Affectation de noms](../../../docs/standard/design-guidelines/naming-guidelines.md)
