---
title: "Langage des expressions régulières - Aide-mémoire"
description: "Langage des expressions régulières - Aide-mémoire"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/28/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 8c5dee8c-7bc7-4e6e-aff1-986965c4d98e
translationtype: Human Translation
ms.sourcegitcommit: 3845ec46cbd1f65abd9b78f7b81487efed9de2f2
ms.openlocfilehash: a6644fc2431beafa2128287eeac73bd598ee304a
ms.lasthandoff: 03/13/2017

---

# <a name="regular-expression-language---quick-reference"></a>Langage des expressions régulières - Aide-mémoire

Une expression régulière est un modèle que le moteur des expressions régulières tente de faire correspondre dans le texte d’entrée. Un modèle se compose d’un ou de plusieurs littéraux de caractère, opérateurs ou constructions. Pour obtenir une brève présentation, consultez [Expressions régulières dans .NET](regular-expressions.md). 

Chaque section dans cette référence rapide répertorie une catégorie particulière de caractères, d'opérateurs et de constructions que vous pouvez utiliser pour définir des expressions régulières : 

* [Caractères d’échappement](#character-escapes)

* [Classes de caractères](#character-classes)
      
* [Ancres](#anchors)
    
* [Constructions de regroupement](#grouping-constructs)
      
* [Quantificateurs](#quantifiers)
    
* [Constructions de référence arrière](#backreference-constructs)
      
* [Constructions d'alternative](#alternation-constructs)
     
* [Substitutions](#substitutions)
      
* [Options des expressions régulières](#regular-expression-options)
      
* [Constructions diverses](#miscellaneous-constructs)

Ces informations sont également disponibles dans deux documents de référence, que vous pouvez télécharger et imprimer : 

* [Télécharger au format Word (.docx)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
    
* [Télécharger au format PDF (.pdf)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
    
## <a name="character-escapes"></a>Caractères d'échappement

La barre oblique inverse (\) dans une expression régulière indique que le caractère qui le suit est un caractère spécial (comme indiqué dans le tableau suivant), ou qu’il doit être interprété littéralement. Pour plus d’informations, consultez [Caractères d’échappement dans les expressions régulières](escapes.md). 

Caractère d'échappement | Description | Modèle | Correspondances
----------------- | ----------- | ------- | -------
**\a** | Correspond à un caractère de cloche, \u0007. | `\a` | "\u0007" dans "Erreur !" + ’\u0007’
**\b** | Dans une classe de caractères, correspond à un retour arrière, \u0008. | `[\b]{3,}` | "\b\b\b\b" dans "\b\b\b\b"
**\t** | Correspond à une tabulation, \u0009. | `(\w+)\t` | "item1\t", "item2\t" dans "item1\titem2\t"
**\r** | Correspond à un retour chariot, \u000D. (**\r** n’est pas équivalent au caractère de saut de ligne, **\n**.) | `\r\n(\w+)` | "\r\nCe" dans "\r\nCe sont\ndeux lignes."
**\v** | Correspond à une tabulation verticale, \u000B. | `[\v]{2,}` | "\v\v\v" dans "\v\v\v"
**\f** | Correspond à un saut de page, \u000C. | `[\f]{2,}` | "\f\f\f" dans "\f\f\f" 
**\n** | Correspond à une nouvelle ligne, \u000A. | `\r\n(\w+)` | "\r\nCe" dans "\r\nCe sont\ndeux lignes."
**\e** | Correspond à un caractère d'échappement, \u001B. | `\e` | "\x001B" dans "\x001B"
**\**_nnn_ | Utilise la représentation octale pour spécifier un caractère (*nnn* se compose de deux ou trois chiffres). | `\w\040\w` | « a b », « c d » dans « a bc d »
**\x**_nn_ | Utilise une représentation hexadécimale pour spécifier un caractère (*nn* se compose de deux chiffres exactement). | `\w\x20\w` | « a b », « c d » dans « a bc d »
**\c**_X_ ou **\c**_x_ | Correspond au caractère de contrôle ASCII spécifié par *X* ou *x*, où *X* ou *x* représente la lettre du caractère de contrôle. | `\cC` | "\x0003" dans "\x0003" (Ctrl-C) 
**\u**_nnnn_ | Correspond à un caractère Unicode en utilisant la représentation hexadécimale (quatre chiffres exactement, représentés par *nnnn*). | `\w\u0020\w` | « a b », « c d » dans « a bc d »
**\\** | Lorsque ce caractère d'échappement est suivi d'un caractère non identifié comme caractère d'échappement, correspond au caractère lui-même. Par exemple, __\*__ est identique à **\x2A**, et **\.** est identique à **\x2E**. Cela permet au moteur d’expression régulière de lever l’ambiguïté d’éléments de langage (tels que `*` ou `?`) et de caractères littéraux (représentés par `\*` or `\?)`. | `\d+[\+-x\*]\d+` | « 2+2 » et « 3*9 » dans « (2+2) * 3*9 »
 
## <a name="character-classes"></a>Classes de caractères

Une classe de caractères fait correspondre tout caractère d'un jeu de caractères. Les classes de caractères incluent les éléments de langage répertoriés dans le tableau suivant. Pour plus d’informations, consultez [Classes de caractères dans les expressions régulières](classes.md).

Classe de caractères | Description | Modèle | Correspondances
--------------- | ----------- | ------- | ------- 
__[__*groupe_caractères*__]__ | Correspond à n’importe quel caractère unique de groupe_caractères. Par défaut, la correspondance respecte la casse. | `[ae]` | « a » dans « gras » ; « a », « e » dans « laine »
__[^__*groupe_caractères*__]__ | Négation : correspond à n’importe quel caractère unique qui ne se trouve pas dans *groupe_caractères*. Par défaut, les caractères de *groupe_caractères* respectent la casse. | `[^aei]` |  "r", "g", "n" dans "règne"
__[__*premier-dernier*__]__ | Plage de caractères : correspond à n’importe quel caractère unique dans la plage comprise entre *premier* et *dernier*. | `[A-Z]` | "A", "B" dans "AB123"
**.** | Caractère générique : correspond à tout caractère à l'exception de \n. Pour faire correspondre un caractère littéral « point » (. ou \u002E), vous devez le faire précéder du caractère d’échappement (\.). | `a.e` |  « ave » dans « navet », « ate » dans « plate »
__\p{__*nom*__}__ | Correspond à n’importe quel caractère unique de la catégorie générale Unicode ou du bloc nommé spécifié par *nom*. | `\p{Lu}`, `\p{IsCyrillic}` | « M », « G » dans « Mardi Gras » ; « ? », « ? » dans « ??em »
__\P{__*nom*__}__ | Correspond à n’importe quel caractère unique qui ne se trouve pas dans la catégorie générale Unicode ou le bloc nommé spécifié par *nom*. | `\P{Lu}`, `\P{IsCyrillic}` |« a », « r », « d », « i » dans « Mardi », « e », « m » dans « ??em »
**\w** | Correspond à n'importe quel caractère alphabétique. | `\w` | "I", "D", "A", "1", "3" dans "ID A1.3" 
**\W** | Correspond à tout caractère autre qu'un caractère de mot. | `\W` | " ", "." dans "ID A1.3"
**\s** | Correspond à tout caractère espace blanc. | `\w\s` | "D " dans "ID A1.3"
**\S** | Correspond à tout caractère autre qu'un espace blanc. | `\s\S` | " _" dans "int __ctr" 
**\d** | Correspond à n'importe quel chiffre décimal. | `\d` | "4" dans "4 = IV" 
**\D** | Correspond à n'importe quel caractère autre qu'un chiffre décimal. | `\D` | " ", "=", " ", "I", "V" dans "4 = IV" 

## <a name="anchors"></a>Ancres

Les ancres, ou assertions de largeur nulle atomiques, entraînent le succès ou l'échec d'une correspondance en fonction de la position actuelle dans la chaîne, mais elles n'entraînent pas l'avancement du moteur à travers la chaîne ou la consommation de caractères. Les métacaractères répertoriés dans le tableau suivant sont des ancres. Pour plus d’informations, consultez [Ancres dans les expressions régulières](anchors.md).

Assertion | Description | Modèle | Correspondances
--------- | ----------- | ------- | ------- 
**^** | La correspondance doit commencer au début de la chaîne ou de la ligne. | `^\d{3}` | « 901 » dans « 901-333- »
**$** | La correspondance doit se produire à la fin de la chaîne ou avant **\n** à la fin de la ligne ou de la chaîne. | `-\d{3}$` | « -333 » dans « -901-333 »
**\A** | La correspondance doit se produire au début de la chaîne. | `\A\d{3}` | « 901 » dans « 901-333- »
**\Z** | La correspondance doit se produire à la fin de la chaîne ou avant **\n** à la fin de la chaîne. | `-\d{3}\Z` | « -333 » dans « -901-333 »
**\z** | La correspondance doit se produire à la fin de la chaîne. | `-\d{3}\z` | « -333 » dans « -901-333 »
**\G** | La correspondance doit se produire à l'emplacement où la correspondance précédente s'est terminée. | `\G\(\d\)` | « (1) », « (3) », « (5) » dans « (1)(3)(5)[7]&#40;9) »
**\b** | La correspondance doit se produire sur une limite entre un caractère **\w** (alphanumérique) et un caractère **\W** (non alphanumérique). | `\b\w+\s\w+\b` | "thèm thème", "thèm thèm" dans "thèm thème thèm thèm" 
**\B** | La correspondance ne doit pas se produire sur une limite **\b**. | `\Bend\w*\b` | "ends", "ender" dans "end sends endure lender"

## <a name="grouping-constructs"></a>Constructions de regroupement

Les constructions de regroupement délimitent les sous-expressions d'une expression régulière et capturent généralement les sous-chaînes d'une chaîne d'entrée. Les constructions de regroupement incluent les éléments de langage répertoriés dans le tableau suivant. Pour plus d’informations, consultez [Constructions de regroupement dans les expressions régulières](grouping.md).

Construction de regroupement | Description | Modèle | Correspondances
------------------ | ----------- | ------- | ------- 
**(**_sous-expression_**)** | Capture la sous-expression mise en correspondance et lui assigne un nombre ordinal de base un. | `(\w)\1` | "oo" dans "boot"
**(?**<name> _sous-expression_**)** | Capture la sous-expression mise en correspondance dans un groupe nommé. | `(?<double>\w)\k<double>` | "oo" dans "boot"
**(?**<nom1-nom2> _sous-expression_**)** | Définit un équilibre de définition de groupe. Pour plus d’informations, consultez la section [Définitions de groupe d’équilibrage](grouping.md#balancing-group-definitions) dans [Constructions de regroupement dans les expressions régulières](grouping.md). | `(((?'Open'\()[^\(\)]*)+((?'Close-Open'\))[^\(\)]*)+)*(?(Open)(?!))$` | « ((1-3)*(3-1)) » dans « 3+2^((1-3)*(3-1)) »
**(?**: sous-expression**)** | Définit un groupe sans capture. | `Write(?:Line)?` | « WriteLine » dans « Console.WriteLine() », « Write » dans « Console.Write(value) »
**(?imnsx-imnsx**: _sous-expression_**)** | Active ou désactive les options spécifiées dans _sous-expression_. Pour plus d’informations, consultez [Options des expressions régulières](options.md). | `A\d{2}(?i:\w+)\b` | "A12xl", "A12XL" dans "A12xl A12XL a12xl"
**(?**= _sous-expression_**)** | Assertion de préanalyse positive de largeur nulle. | `\w+(?=\.)` | "est", "courait", et "couché" dans "Il est. Le chien courait. Le soleil est couché."
**(?!** _sous-expression_**)** | Assertion de préanalyse négative de largeur nulle. | `\b(?!un)\w+\b` | "retourner", "utilisée" dans "retourner une unité utilisée"
**(?**<= _sous-expression_**)** | Assertion de postanalyse positive de largeur nulle. | `(?<=19)\d{2}\b` | "99", "50", "05" dans "1851 1999 1950 1905 2003"
**(?**<! _sous-expression_**)** | Assertion de postanalyse négative de largeur nulle. | `(?<!19)\d{2}\b` | "51", "03" dans "1851 1999 1950 1905 2003"
**(?**> _sous-expression_**)** | Sous-expressions de recherche non rétroactive (ou « gourmandes »). | `[13579](?>A+B+)` | "1ABB", "3ABB" et "5AB" dans "1ABB 3ABBC 5AB 5AC"

## <a name="quantifiers"></a>Quantificateurs

Un quantificateur indique combien d'instances de l'élément précédent (qui peut être un caractère, un groupe ou une classe de caractères) doivent être présentes dans la chaîne d'entrée pour qu'il y ait correspondance. Les quantificateurs incluent les éléments de langage répertoriés dans le tableau suivant. Pour plus d’informations, consultez [Quantificateurs dans les expressions régulières](quantifiers.md).

Quantifieur | Description | Modèle | Correspondances
---------- | ----------- | ------- | -------
__*__ | Correspond zéro, une ou plusieurs fois à l'élément précédent. | `\d*\.\d` | ".0", "19.9", "219.9"
**+** | Correspond une ou plusieurs fois à l'élément précédent. | `"be+"` | "bee" dans "beefsteak", "be" dans "besoin"
**?** | Correspond zéro ou une fois à l'élément précédent. | `"rai?n"` | "rang", "train"
**{**_n_**}** | Correspond à l’élément précédent exactement *n* fois. | `",\d{3}"` | ",043" dans "1,043.6", ",876", ",543" et ",210" dans "9,876,543,210"
**{**_n_,**}** | Correspond à l’élément précédent au moins *n* fois. | `"\d{2,}"` | "166", "29", "1930"
**{**_n_,_m_**}** | Correspond à l’élément précédent au moins *n* fois, mais pas plus de *m* fois. | `"\d{3,5}"` | « 166 », « 17668 » ; « 19302 » dans « 193024 »
__*?__ | Correspond zéro fois ou plus à l'élément précédent, mais le moins de fois possible. | `\d*?\.\d` | ".0", "19.9", "219.9"
**+?** | Correspond une ou plusieurs fois à l'élément précédent, mais le moins de fois possible. | `"be+?"` | "bee" dans "beefsteak", "be" dans "besoin"
**??** | Correspond zéro ou une fois à l'élément précédent, mais le moins de fois possible. | `"rai??n"` | "rang", "train"
**{**_n_**}?** | Correspond exactement *n* fois à l’élément précédent. | `",\d{3}?"` | ",043" dans "1,043.6", ",876", ",543" et ",210" dans "9,876,543,210"
**{**_n_,**}?** | Correspond au moins *n* fois à l’élément précédent, mais le moins de fois possible. | `"\d{2,}?"` | "166", "29", "1930"
**{**_n_,_m_**}?** | Correspond entre *n* et *m* fois à l’élément précédent, mais le moins de fois possible. | `"\d{3,5}?"` | « 166 », « 17668 » ; « 193 », « 024 » dans « 193024 »

## <a name="backreference-constructs"></a>Constructions de backreference

Une backreference permet qu'une sous-expression précédemment mise en correspondance soit ensuite identifiée dans la même expression régulière. Le tableau suivant répertorie les constructions de backreference prises en charge par les expressions régulières dans le .NET Framework. Pour plus d’informations, consultez [Constructions de références arrière dans les expressions régulières](backreference.md).

Construction de backreference | Description | Modèle | Correspondances
----------------------- | ----------- | ------- | -------
**\**_numéro_ | Backreference. Correspond à la valeur d'une sous-expression numérotée. | `(\w)\1    ` | "ee" dans "seek"
**\k<**_nom_**>** | Backreference nommée. Correspond à la valeur d'une expression nommée. | `(?<char>\w)\k<char>` | "ee" dans "seek"

## <a name="alternation-constructs"></a>Constructions d'alternative

Les constructions d'alternative modifient une expression régulière pour permettre la correspondance de type inclusif/exclusif. Ces constructions incluent les éléments de langage répertoriés dans le tableau suivant. Pour plus d’informations, consultez [Constructions d’alternative dans les expressions régulières](alternation.md).

Construction d'alternative | Description | Modèle | Correspondances
--------------------- | ----------- | ------- | ------- 
**&#124;** | Correspond à tout élément séparé par le caractère barre verticale (*&#124;). | `th(e*&#124;is*&#124;at)` | "the", "this" dans "this is the day. " "
__(?(__*expression*__)__*oui*__&#124;__*non*__)__ | Correspond à *oui* si le modèle d’expression régulière indiqué par *expression* correspond ; sinon, correspond à *non* (facultatif). *expression* est interprétée comme une assertion de largeur nulle. | `(?(A)A\d{2}\b*&#124;\b\d{3}\b)` | "A10", "910" dans "A10 C103 910"
**(?(**_nom_**)**_oui_&#124;_non_**)** | Correspond à *oui* si *nom*, un groupe de capture nommé ou numéroté, a une correspondance ; sinon, correspond à *non* (facultatif). | `(?<quoted>")?(?,(quoted).+?"*&#124;\S+\s)` | Dogs.jpg, "Yiska playing.jpg" dans "Dogs.jpg "Yiska playing.jpg""

## <a name="substitutions"></a>Substitutions

Les substitutions sont des éléments de langage d’expression régulière pris en charge dans les modèles de remplacement. Pour plus d’informations, consultez [Substitutions dans les expressions régulières](substitutions.md). Les métacaractères répertoriés dans le tableau suivant sont des assertions de largeur nulle atomiques.

Caractère | Description | Modèle | Modèle de remplacement | Chaîne d'entrée | Chaîne de résultat
--------- | ----------- | ------- | ------------------- | ------------ | ------------- 
**$**_nombre_ | Remplace la sous-chaîne mise en correspondance par le groupe *nombre*. | `\b(\w+)(\s)(\w+)\b` | `$3$2$1` | "un deux" | "deux un"
**${**_nom_**}** | Remplace la sous-chaîne mise en correspondance par le groupe nommé *nom*. | `\b(?<word1>\w+)(\s)(?<word2>\w+)\b` | `${word2} ${word1}` | "un deux" | "deux un"
**$$** | Remplace un "$" littéral. | `\b(\d+)\s?USD` | `$$$1` | "103 USD" | "$103"
**$&** | Remplace une copie de la totalité de la correspondance. | `\$?\d*\.?\d+` | `**$&**` | "$1.30" | "**$1.30**"
**$`** | Remplace tout le texte de la chaîne d'entrée avant la correspondance. | `B+` | `$`` | "AABBCC" | "AAAACC"
**$'** | Remplace tout le texte de la chaîne d'entrée après la correspondance. | `B+` | `$'` | "AABBCC" | "AACCCC"
**$+** | Remplace le dernier groupe qui a été capturé. | `B+(C+)` | `$+` | "AABBCCDD" | "AACCDD"
**$_** | Remplace la chaîne d'entrée entière. | `B+` | `$_` | "AABBCC" | "AAAABBCCCC"

## <a name="regular-expression-options"></a>Options des expressions régulières

Vous pouvez définir des options qui contrôlent comment le moteur des expressions régulières interprète un modèle d'expression régulière. Bon nombre de ces options peuvent être spécifiées inline (dans le modèle d'expression régulière) ou sous la forme d'une ou de plusieurs constantes `RegexOptions`. Cette référence rapide répertorie uniquement les options inline. Pour plus d’informations sur les options inline et `RegexOptions`, consultez l’article [Options des expressions régulières](options.md). 

Vous pouvez spécifier une option inline de deux façons :

* À l’aide d’une construction diverse **(?imnsx-imnsx)**, où un signe moins (-) devant une option ou un jeu d’options désactive ces options. Par exemple, **(?i-mn)** active la correspondance qui ne respecte pas la casse (i), désactive le mode multiligne (**m**) et désactive les captures de groupe sans nom (**n**). L’option s’applique au modèle d’expression régulière depuis le point au niveau duquel l’option est définie et est effective jusqu’à la fin du modèle ou jusqu’au point au niveau duquel une autre construction inverse l’option.

* À l’aide de la construction de regroupement **(?imnsx-imnsx:**_sous-expression_**)**, qui définit des options uniquement pour le groupe spécifié.

Le moteur d’expression régulière de .NET prend en charge les options inline suivantes.

Option | Description | Modèle | Correspondances
------ | ----------- | ------- | ------- 
**i** | Utilise la correspondance qui ne respecte pas la casse. | **\b(?i)a(?-i)a\w+\b** | « aardvark », « aaaAuto » dans « aardvark AAAuto aaaAuto Adam breakfast » 
**m** | Utilise le mode multiligne. **^** et **$** correspondent au début et à la fin d’une ligne, au lieu du début et de la fin d’une chaîne. | Pour obtenir un exemple, consultez la section « Mode multiligne » dans [Options des expressions régulières](options.md). | 
**n*** | Ne capture aucun groupe sans nom. | Pour obtenir un exemple, consultez la section « Captures explicites uniquement » dans [Options des expressions régulières](options.md). | 
**s** | Utilise le mode à ligne simple. | Pour obtenir un exemple, consultez la section « Mode à ligne simple » dans [Options des expressions régulières](options.md). | 
**x** | Ignore l’espace blanc sans séquence d’échappement dans le modèle d’expression régulière. | **\b(?x) \d+ \s \w+** | « 1 aardvark », « 2 cats » dans « 1 aardvark 2 cats IV centurions » 

##<a name="miscellaneous-constructs"></a>Constructions diverses

Diverses constructions modifient un modèle d’expression régulière ou fournissent des informations le concernant. Le tableau suivant répertorie les diverses constructions prises en charge par .NET. Pour plus d’informations, consultez [Constructions diverses dans les expressions régulières](miscellaneous.md).

Construction | Définition | Exemple
--------- | ---------- | ------- 
**(?imnsx-imnsx)** | Active ou désactive des options telles que le non-respect de la casse au milieu d’un modèle. Pour plus d’informations, consultez [Options des expressions régulières](options.md). | `\bA(?i)b\w+\b` correspond à "ABA", "Able" dans "ABA Able Act"
**(?#** _commentaire_**)** | Commentaire inline. Le commentaire se termine à la première parenthèse fermante. | `\bA(?#` correspond aux mots commençant par `A)\w+\b`
**#** [jusqu’à la fin de la ligne] | Commentaire en mode X. Le commentaire commence au caractère # sans séquence d’échappement et se poursuit jusqu’à la fin de la ligne. | `(?x)\bA\w+\b#` correspond aux mots commençant par `A`

## <a name="see-also"></a>Voir aussi




[System.Text.RegularExpressions](xref:System.Text.RegularExpressions)

[Regex](xref:System.Text.RegularExpressions.Regex)

[Expressions régulières dans .NET](regular-expressions.md)

[Modèle objet d’expression régulière](object-model.md)

[Exemples d’expressions régulières](regex-examples.md)

[Télécharger au format Word (.docx)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)
    
[Télécharger au format PDF (.pdf)](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)

