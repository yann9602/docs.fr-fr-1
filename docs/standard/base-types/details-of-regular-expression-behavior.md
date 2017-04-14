---
title: "Comportement d&#233;taill&#233; des expressions r&#233;guli&#232;res | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "expressions régulières, comportement"
  - "expressions régulières du .NET Framework, comportement"
ms.assetid: 0ee1a6b8-caac-41d2-917f-d35570021b10
caps.latest.revision: 27
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 27
---
# Comportement d&#233;taill&#233; des expressions r&#233;guli&#232;res
Le moteur de traitement des expressions régulières du .NET Framework est un outil de recherche qui fait appel aux expressions régulières en procédant par rétroaction. Cet outil intègre un moteur classique de type NFA \(Nondeterministic Finite Automaton\) similaire à celui utilisé par Perl, Python, Emacs et Tcl.  C'est ce qui le différencie des moteurs de traitement des expressions régulières pures de type DFA \(Deterministic Finite Automaton\), plus rapides mais également plus limités, que l'on trouve dans awk, egrep ou lex.  C'est également ce qui le différencie des moteurs NFA POSIX, standard, mais qui sont plus lents.  La section suivante décrit les trois types de moteurs des expressions régulières et explique pourquoi les expressions régulières du .NET Framework sont implémentées à l'aide d'un moteur NFA classique.  
  
## Avantages du moteur NFA  
 Lorsque les moteurs DFA exécutent la correspondance de modèles, leur ordre de traitement est déterminé par la chaîne d'entrée.  Le moteur commence au début de la chaîne d'entrée et continue de manière séquentielle pour déterminer si le caractère suivant correspond au modèle d'expression régulière.  Ces moteurs peuvent garantir une correspondance avec la plus longue chaîne possible.  Étant donné qu'ils ne testent jamais le même caractère deux fois, les moteurs DFA ne prennent pas en charge la rétroaction.  Toutefois, comme un moteur DFA prend uniquement en compte un état fini, il ne peut pas rechercher un modèle avec références arrière, et comme il ne construit pas d'expansion explicite, il ne peut pas non plus capturer de sous\-expressions.  
  
 Contrairement aux moteurs DFA, lorsque les moteurs NFA classiques effectuent une correspondance de modèles, leur ordre de traitement est déterminé par le modèle d'expression régulière.  Lorsqu'il traite un élément de langage particulier, le moteur utilise une correspondance gourmande ; autrement dit, il recherche le maximum de la chaîne d'entrée possible.  Mais il enregistre également son état après trouvé la correspondance d'une sous\-expression.  Si une correspondance finit par échouer, le moteur peut retourner à un état enregistré pour tenter d'autres correspondances.  Ce processus consistant à abandonner une correspondance réussie de sous\-expression pour que les éléments de langage suivants dans l'expression régulière puissent également correspondre est appelé *rétroaction*.  Les moteurs NFA utilisent la rétroaction pour tester toutes les expansions possibles d'une expression régulière dans un ordre spécifique et accepter la première correspondance.  Comme un moteur NFA classique procède à une expansion spécifique des expressions régulières pour obtenir une correspondance, il peut capturer des occurrences de sous\-expressions et de références arrière.  Cependant, étant donné qu'un moteur NFA classique recherche par rétroaction, il peut visiter exactement le même état plusieurs fois si l'état est accessible via différents chemins.  Son exécution risque ainsi de se ralentir considérablement.  Comme un moteur NFA classique accepte la première correspondance trouvée, il peut également en négliger d'autres \(éventuellement plus longues\).  
  
 Les moteurs NFA POSIX sont similaires aux moteurs NFA classiques, à la différence qu'ils continuent de rechercher rétroactivement jusqu'à ce qu'ils aient trouvé de façon certaine la correspondance la plus longue possible.  C'est la raison pour laquelle un moteur NFA POSIX est plus lent qu'un moteur NFA classique et, si vous utilisez un moteur NFA POSIX, il est impossible de préférer la correspondance la plus courte en changeant l'ordre de la recherche rétroactive.  
  
 Les moteurs NFA classiques ont la préférence des programmeurs parce qu'ils permettent de mieux contrôler la recherche de chaînes que les moteurs DFA ou NFA POSIX.  Même si leur exécution est parfois très lente, il reste possible de les amener à effectuer des recherches en mode linéaire ou polynomial à l'aide de modèles propres à limiter les ambiguïtés et à réduire la rétroaction.  En d'autres termes, bien que les moteurs NFA privilégient les performances au détriment de la rapidité et de la flexibilité, ils offrent souvent des performances acceptables si une expression régulière est correctement écrite et évite des casses susceptibles de nuire exponentiellement à l'efficacité de la rétroaction.  
  
> [!NOTE]
>  Pour plus d'informations sur les pertes en termes de performances entraînées par une rétroaction excessive et les moyens de créer des expressions régulières pour les contourner, consultez [Rétroaction](../../../docs/standard/base-types/backtracking-in-regular-expressions.md).  
  
## Possibilités du moteur du .NET Framework  
 Le moteur de traitement des expressions régulières du .NET Framework propose un ensemble complet de constructions pour permettre aux programmeurs de diriger le moteur de recherche rétroactive et de tirer parti d'un moteur NFA classique.  Ces constructions peuvent servir à rechercher des correspondances plus rapidement ou à indiquer la priorité d'expansions spécifiques par rapport à d'autres.  
  
 Le moteur de traitement des expressions régulières du .NET Framework inclut également les fonctionnalités suivantes :  
  
-   quantifieurs lents: `??`, `*?`, `+?`, `{`*n*`,`*m*`}?`.  Ces constructions indiquent au moteur de recherche rétroactive de rechercher d'abord le nombre minimal de répétitions.  Par opposition, les quantificateurs gourmands ordinaires essaient de trouver d'abord le nombre maximal de répétitions.  L'exemple suivant illustre la différence entre les deux.  Une expression régulière correspond à une phrase se terminant par un nombre, qu'un groupe de capture permet d'extraire.  L'expression régulière `.+(\d+)\.` inclut le quantificateur gourmand `.+`, qui indique au moteur des expressions régulières de capturer uniquement le dernier chiffre du nombre.  Par opposition, l'expression régulière `.+?(\d+)\.` inclut le quantificateur paresseux `.+?`, qui indique au moteur des expressions régulières de capturer le nombre entier.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lazy1.cs#1)]
     [!code-vb[Conceptual.RegularExpressions.Design#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lazy1.vb#1)]  
  
     Les versions gourmande et paresseuse de cette expression régulière sont définies comme indiqué dans le tableau suivant.  
  
    |Modèle|Description|  
    |------------|-----------------|  
    |`.+` \(quantificateur gourmand\)|Établit une correspondance avec au moins une occurrence d'un caractère.  Le moteur des expressions régulières établit ainsi une correspondance avec la chaîne entière, puis effectue autant de recherches rétroactives que nécessaires pour trouver le reste du modèle.|  
    |`.+?` \(quantificateur paresseux\)|Établit une correspondance avec au moins une occurrence d'un caractère, mais recherche le minimum de correspondances possibles.|  
    |`(\d+)`|Établit une correspondance avec au moins un chiffre et l'attribue au premier groupe de capture.|  
    |`\.`|Mettre en correspondance un point.|  
  
     Pour plus d'informations sur les quantificateurs paresseux, consultez [Quantificateurs](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md).  
  
-   Préanalyse positive: `(?=`*subexpression*`)`.  Cette fonctionnalité permet au moteur de recherche rétroactive de retourner au même endroit dans le texte après avoir trouvé la correspondance d'une sous\-expression.  Elle est utile pour effectuer une recherche dans le texte en vérifiant plusieurs modèles à partir d'une même position.  Elle permet également au moteur de vérifier qu'une sous\-chaîne existe à la fin de la correspondance sans inclure la sous\-chaîne dans le texte trouvé.  L'exemple suivant utilise la préanalyse positive pour extraire les mots d'une phrase qui ne sont pas suivis de symboles de ponctuation.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead1.cs#2)]
     [!code-vb[Conceptual.RegularExpressions.Design#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead1.vb#2)]  
  
     L'expression régulière `\b[A-Z]+\b(?=\P{P})` est définie comme indiqué dans le tableau suivant.  
  
    |Modèle|Description|  
    |------------|-----------------|  
    |`\b`|Commencer la correspondance à la limite d'un mot.|  
    |`[A-Z]+`|Établit une ou plusieurs fois la correspondance avec un caractère alphabétique.  Étant donné que la méthode <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=fullName> est appelée avec l'option <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>, la comparaison n'est pas sensible à la casse.|  
    |`\b`|Terminer la correspondance à la limite d'un mot.|  
    |`(?=\P{P})`|Effectue une préanalyse pour déterminer si le caractère suivant est un symbole de ponctuation.  Si ce n'est pas le cas, la correspondance réussit.|  
  
     Pour plus d'informations sur les assertions de préanalyse positive, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Préanalyse négative. `(?!`*subexpression*`)`.  Cette fonctionnalité ajoute la possibilité de retrouver une expression uniquement si une sous\-expression n'a pas de correspondance.  Elle est particulièrement efficace pour affiner une recherche, étant donné qu'une expression correspondant à un cas à éliminer est souvent beaucoup plus simple qu'une expression correspondant à des cas à inclure.  Par exemple, il est difficile d'écrire une expression pour les mots ne commençant pas par « non ».  L'exemple suivant utilise la préanalyse négative pour les exclure.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookahead2.cs#3)]
     [!code-vb[Conceptual.RegularExpressions.Design#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookahead2.vb#3)]  
  
     Le modèle d'expression régulière `\b(?!non)\w+\b` est défini comme indiqué dans le tableau suivant.  
  
    |Modèle|Description|  
    |------------|-----------------|  
    |`\b`|Commencer la correspondance à la limite d'un mot.|  
    |`(?!non)`|Effectue une préanalyse pour vérifier que la chaîne actuelle ne commence pas par « non ».  Le cas échéant, la correspondance échoue.|  
    |`(\w+)`|Mettre en correspondance un ou plusieurs caractères alphabétiques.|  
    |`\b`|Terminer la correspondance à la limite d'un mot.|  
  
     Pour plus d'informations sur les assertions de préanalyse négative, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Évaluation conditionnelle : `(?(`*expression*`)`*yes* `|` *no* `)` et `(?(`*name*`)`*yes* `|` *no* `)`, où l'expression *expression* est une sous\-expression à rechercher, *name* est le nom d'un groupe de capture, *yes* est la chaîne à rechercher si une correspondance est établie pour *expression* ou si *name* est un groupe capturé valide et non vide, et *no* est la sous\-expression à rechercher si aucune correspondance n'est établie pour *expression* ou si *name* n'est pas un groupe capturé valide et non vide.  Cette fonctionnalité permet au moteur d'effectuer une recherche à l'aide de plusieurs autres modèles, selon le résultat d'une correspondance de sous\-expression précédente ou le résultat d'une assertion de largeur nulle.  Par exemple, un formulaire de référence arrière plus puissant peut ainsi rechercher une sous\-expression selon qu'une sous\-expression précédente a été trouvée ou non.  L'expression régulière de l'exemple suivant établit une correspondance avec des paragraphes destinés à un usage public et interne.  Les paragraphes prévus uniquement pour un usage interne commencent par une balise `<PRIVATE>`.  Le modèle d'expression régulière `^(?<Pvt>\<PRIVATE\>\s)?(?(Pvt)((\w+\p{P}?\s)+)|((\w+\p{P}?\s)+))\r?$` utilise une évaluation conditionnelle pour assigner le contenu des paragraphes destinés à un usage public et interne à des groupes de capture différents.  Ces paragraphes peuvent ensuite être gérés séparément.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/conditional1.cs#4)]
     [!code-vb[Conceptual.RegularExpressions.Design#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/conditional1.vb#4)]  
  
     Le modèle d'expression régulière est défini comme indiqué dans le tableau suivant.  
  
    |Modèle|Description|  
    |------------|-----------------|  
    |`^`|Commence la correspondance au début d'une ligne.|  
    |`(?<Pvt>\<PRIVATE\>\s)?`|Établit une correspondance avec zéro, une ou plusieurs occurrences de la chaîne `<PRIVATE>`, suivie d'un espace.  Assigne la correspondance à un groupe de capture nommé `Pvt`.|  
    |`(?(Pvt)((\w+\p{P}?\s)+)`|Si le groupe de capture `Pvt` existe, établit la correspondance avec une ou plusieurs occurrences d'un ou plusieurs caractères alphabétiques suivis de zéro ou un séparateur de ponctuation suivi d'un espace.  Assigne la sous\-chaîne au premier groupe de capture.|  
    |`&#124;((\w+\p{P}?\s)+))`|Si le groupe de capture `Pvt` n'existe pas, établit la correspondance avec une ou plusieurs occurrences d'un ou plusieurs caractères alphabétiques suivis de zéro ou un séparateur de ponctuation suivi d'un espace.  Assigne la sous\-chaîne au troisième groupe de capture.|  
    |`\r?$`|Établit une correspondance avec la fin d'une ligne ou d'une chaîne.|  
  
     Pour plus d'informations sur l'évaluation conditionnelle, consultez [Constructions d'alternative](../../../docs/standard/base-types/alternation-constructs-in-regular-expressions.md).  
  
-   Définitions de groupes d'équilibrage: `(?<`*name1*`-`*name2*`>` *subexpression*`)`.  Cette fonctionnalité permet au moteur des expressions régulières suivre des constructions imbriquées, telles que des parenthèses ou des crochets ouvrants et fermants.  Pour obtenir un exemple, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Sous\-expressions de recherche non rétroactive \(également appelées sous\-expressions gourmandes\) : `(?>`*subexpression*`)`.  Cette fonctionnalité permet au moteur de recherche non rétroactive de vérifier qu'une sous\-expression correspond uniquement à la première occurrence trouvée pour cette sous\-expression, comme si l'expression s'exécutait indépendamment de l'expression qui la contient.  Sans cette construction, les recherches rétroactives à partir de la plus longue expression peuvent modifier le comportement d'une sous\-expression.  Par exemple, l'expression régulière `(a+)\w` correspond à un ou plusieurs caractères« a », ainsi qu'à un caractère alphabétique suivant la séquence de caractères « a », et assigne la séquence de caractères « a » au premier groupe de capture. Toutefois, si le dernier caractère de la chaîne d'entrée est également un « a », il est associé à l'élément de langage `\w` et n'est pas inclus dans le groupe capturé.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.Design#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking2.vb#7)]  
  
     L'expression régulière `((?>a+))\w` empêche ce comportement.  Étant donné que tous les caractères « a » consécutifs sont trouvés sans rétroaction, le premier groupe de capture inclut tous les caractères « a » consécutifs.  Si les caractères « a » ne sont pas suivis d'au moins un caractère supplémentaire autre que « a », la correspondance échoue.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/nonbacktracking1.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.Design#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/nonbacktracking1.vb#8)]  
  
     Pour plus d'informations sur les sous\-expressions de recherche non rétroactive, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
-   Recherche de correspondances de droite à gauche \(spécifiée en attribuant l'option <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> à un constructeur de classe <xref:System.Text.RegularExpressions.Regex> ou à une méthode de correspondance d'instance statique.  Cette fonctionnalité est utile lorsque la recherche s'effectue de droite à gauche et non de gauche à droite ou dans les cas où il est plus efficace de lancer une recherche en commençant par la partie droite du modèle qu'en commençant par la gauche.  Comme l'illustre l'exemple suivant, l'utilisation de la recherche de correspondances de droite à gauche peut modifier le comportement des quantificateurs gourmands.  L'exemple effectue deux recherches pour une phrase qui se termine par un nombre.  La recherche de gauche à droite qui utilise le quantificateur gourmand `+` trouve l'un des six chiffres dans la phrase, alors que la recherche de droite à gauche trouve l'ensemble des six chiffres.  Pour une description du modèle d'expression régulière, consultez l'exemple qui illustre les quantificateurs paresseux plus loin dans cette section.  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/rtl1.cs#6)]
     [!code-vb[Conceptual.RegularExpressions.Design#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/rtl1.vb#6)]  
  
     Pour plus d'informations sur la recherche de correspondances de droite à gauche, consultez [Options des expressions régulières](../../../docs/standard/base-types/regular-expression-options.md).  
  
-   Postanalyse positive et négative : `(?<=`*subexpression*`)` pour une postanalyse positive et `(?<!`*subexpression*`)` pour une postanalyse négative.  Cette fonctionnalité est semblable à la préanalyse décrite précédemment dans cette rubrique.  Comme le moteur des expressions régulières permet une recherche complète des correspondances de droite à gauche, les expressions régulières autorisent des postanalyses illimitées.  La postanalyse positive et négative peut également être utilisée pour éviter d'imbriquer des quantificateurs lorsque la sous\-expression imbriquée est un sur\-ensemble d'une expression externe.  Les expressions régulières comportant ces quantificateurs imbriqués offrent souvent des performances médiocres.  L'exemple suivant vérifie qu'une chaîne commence et se termine par un caractère alphanumérique, et que tous les autres caractères de la chaîne sont compris dans un plus grand sous\-ensemble.  Il forme une partie de l'expression régulière utilisée pour valider des adresses de messagerie ; pour plus d'informations, consultez [Comment : vérifier que des chaînes sont dans un format d'adresse de messagerie valide](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
     [!code-csharp[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.design/cs/lookbehind1.cs#5)]
     [!code-vb[Conceptual.RegularExpressions.Design#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.design/vb/lookbehind1.vb#5)]  
  
     L'expression régulière `^[A-Z0-9]([-!#$%&'.*+/=?^`{}|~\w])*(?<=[A-Z0-9])$` est définie comme indiqué dans le tableau suivant.  
  
    |Modèle|Description|  
    |------------|-----------------|  
    |`^`|Commence la correspondance au début de la chaîne.|  
    |`[A-Z0-9]`|Établit une correspondance avec n'importe quel caractère numérique ou alphanumérique. \(La comparaison ne respecte pas la casse.\)|  
    |`([-!#$%&'.*+/=?^`{}&#124;~\w])*`|Établit une correspondance avec zéro, une ou plusieurs occurrences d'un caractère alphabétique ou de l'un des caractères suivants : \-, \!, \#, $, %, &, ', ., \*, \+, \/, \=, ?, ^, \`, {, }, &#124;, or ~.|  
    |`(?<=[A-Z0-9])`|Effectue une postanalyse du caractère précédent, qui doit être numérique ou alphanumérique. \(La comparaison ne respecte pas la casse.\)|  
    |`$`|Termine la correspondance à la fin de la chaîne.|  
  
     Pour plus d'informations sur la postanalyse positive et négative, consultez [Constructions de regroupement](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Rétroaction](../../../docs/standard/base-types/backtracking-in-regular-expressions.md)|Fournit des informations sur la manière dont la rétroaction des expressions régulières crée des branches pour trouver d'autres correspondances.|  
|[Compilation et réutilisation](../../../docs/standard/base-types/compilation-and-reuse-in-regular-expressions.md)|Fournit des informations sur la compilation et la réutilisation des expressions régulières pour augmenter les performances.|  
|[Sécurité des threads](../../../docs/standard/base-types/thread-safety-in-regular-expressions.md)|Fournit des informations sur la sécurité des threads des expressions régulières et explique quand vous devez synchroniser l'accès à des objets d'expressions régulières.|  
|[Expressions régulières du .NET Framework](../../../docs/standard/base-types/regular-expressions.md)|Présente une vue d'ensemble du langage de programmation des expressions régulières.|  
|[Modèle objet d'expression régulière](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Fournit des informations et des exemples de code montrant comment utiliser les classes d'expressions régulières.|  
|[Exemples d'expressions régulières](../../../docs/standard/base-types/regular-expression-examples.md)|Contient des exemples de code qui illustrent l'utilisation d'expressions régulières dans des applications courantes.|  
|[Langage des expressions régulières \- Aide\-mémoire](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Fournit des informations sur l'ensemble des caractères, opérateurs et constructions que vous pouvez utiliser pour définir des expressions régulières.|  
  
## Référence  
 <xref:System.Text.RegularExpressions?displayProperty=fullName>