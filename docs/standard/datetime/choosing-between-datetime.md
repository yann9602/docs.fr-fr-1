---
title: "Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo | Microsoft Docs"
ms.custom: ""
ms.date: "04/10/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DateTimeOffset (structure)"
  - "TimeZoneInfo (classe)"
  - "fuseaux horaires (.NET Framework), utilisations courantes"
  - "classes de date et d'heure (.NET Framework)"
  - "fuseaux horaires (.NET Framework), options de type"
  - "DateTime (structure)"
ms.assetid: 07f17aad-3571-4014-9ef3-b695a86f3800
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo
Les applications [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] qui utilisent des informations de date et d'heure sont très diverses et peuvent utiliser ces informations de plusieurs façons. Les utilisations les plus courantes des informations de date et d'heure sont une ou plusieurs parmi les suivantes :  
  
-   Pour refléter seulement une date, les informations d'heure n'étant pas importantes.  
  
-   Pour refléter seulement une heure, les informations de date n'étant pas importantes.  
  
-   Pour refléter une date et une heure abstraites, qui ne sont pas liées à un moment et un endroit spécifiques \(par exemple, la plupart des magasins d'une chaîne internationale ouvrent en semaine à 9h00\).  
  
-   Pour récupérer les informations de date et d'heure à partir de sources externes au [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], en général là où les informations de date et d'heure sont stockées dans un type de données simple.  
  
-   Pour identifier de façon univoque et non ambiguë un point unique dans le temps. Certaines applications requièrent qu'une date\/heure soit ambiguë seulement sur le système hôte. D'autres requièrent qu'elle soit non ambiguë entre les systèmes \(autrement dit, une date sérialisée sur un système peut être désérialisée de manière significative et utilisée sur un autre système n'importe où dans le monde\).  
  
-   Pour conserver plusieurs dates\/heures ayant un lien les unes avec les autres \(comme la date\/heure locale du demandeur et la date\/heure de réception par le serveur d'une demande web\).  
  
-   Pour effectuer des calculs de date et d'heure, éventuellement avec un résultat qui identifie de façon univoque et non ambiguë un point unique dans le temps.  
  
 Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] comprend les types <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan> et <xref:System.TimeZoneInfo>, tous pouvant être utilisés pour créer des applications qui fonctionnent avec des dates et des heures.  
  
> [!NOTE]
>  Cette rubrique ne traite pas d'un quatrième type, <xref:System.TimeZone>, car ses fonctionnalités sont presqu'entièrement intégrées dans la classe <xref:System.TimeZoneInfo>. Chaque fois que c'est possible, les développeurs doivent utiliser la classe <xref:System.TimeZoneInfo> au lieu de la classe <xref:System.TimeZone>.  
  
## La structure DateTime  
 Une valeur <xref:System.DateTime> définit une date\/heure spécifique. Depuis la version 2.0 du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], elle inclut une propriété <xref:System.DateTime.Kind%2A> qui fournit des informations limitées sur le fuseau horaire à laquelle appartient cette date\/heure. La valeur <xref:System.DateTimeKind> retournée par la propriété <xref:System.DateTime.Kind%2A> indique si la valeur <xref:System.DateTime> représente la date\/heure locale \(<xref:System.DateTimeKind?displayProperty=fullName>\), la date\/heure UTC \(<xref:System.DateTimeKind?displayProperty=fullName>\) ou une date\/heure non spécifiée \(<xref:System.DateTimeKind?displayProperty=fullName>\).  
  
 La structure <xref:System.DateTime> convient pour les applications qui :  
  
-   Utilisent seulement des dates.  
  
-   Utilisent seulement des heures.  
  
-   Utilisent des dates et des heures abstraites.  
  
-   Utilisent des dates et des heures pour lesquelles les informations de fuseau horaire sont manquantes.  
  
-   Utilisent seulement des dates et des heures UTC.  
  
-   Récupèrent des informations de date et d'heure auprès de sources externes au [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], comme des bases de données SQL. En règle générale, ces sources stockent les informations de date et d'heure dans un format simple qui est compatible avec la structure <xref:System.DateTime>.  
  
-   Effectuent des calculs de dates et d'heures, mais sont surtout concernées par des résultats d'ordre général. Par exemple, dans une opération d'addition qui ajoute six mois à une date\/heure, il n'est souvent pas important que le résultat soit ajusté pour l'heure d'été.  
  
 Sauf si une valeur <xref:System.DateTime> particulière représente le temps UTC, cette valeur de date\/heure est souvent ambiguë ou limitée en termes de portabilité. Par exemple, si une valeur <xref:System.DateTime> représente l'heure locale, elle est portable dans ce fuseau horaire local \(c'est\-à\-dire que si la valeur est désérialisée sur un autre système dans le même fuseau horaire, cette valeur continue d'identifier de façon non ambiguë un point unique dans le temps\). En dehors du fuseau horaire local, cette valeur <xref:System.DateTime> peut être interprétée de plusieurs façons. Si la propriété <xref:System.DateTime.Kind%2A> de la valeur est <xref:System.DateTimeKind?displayProperty=fullName>, elle est encore moins portable : elle est maintenant ambiguë dans le même fuseau horaire, voire même sur le système où elle a été sérialisée pour la première fois. Seulement dans le cas où une valeur <xref:System.DateTime> représente le temps UTC, celle\-ci identifie de façon non ambiguë un point unique dans le temps, indépendamment du système ou du fuseau horaire où la valeur est utilisée.  
  
> [!IMPORTANT]
>  Lors de l'enregistrement ou du partage de données <xref:System.DateTime>, le temps UTC doit être utilisé et la propriété <xref:System.DateTime> de la valeur <xref:System.DateTime.Kind%2A> doit être définie à <xref:System.DateTimeKind?displayProperty=fullName>.  
  
## La structure DateTimeOffset  
 La structure <xref:System.DateTimeOffset> représente une valeur de date et d'heure, ainsi qu'un décalage qui indique de combien cette valeur diffère du temps UTC. Ainsi, la valeur toujours identifie toujours de façon non ambiguë un point unique dans le temps.  
  
 Le type <xref:System.DateTimeOffset> comprend toutes les fonctionnalités du type <xref:System.DateTime>, ainsi que la gestion des fuseaux horaires. Il convient donc pour les applications qui :  
  
-   Identifient de façon univoque et non ambiguë un point unique dans le temps. Le type <xref:System.DateTimeOffset> peut être utilisé pour définir de façon non ambiguë la signification de "maintenant", pour consigner les dates\/heures des transactions, pour consigner les dates\/heures des événements système ou des événements d'une application, et pour enregistrer les dates\/heures de création et de modification des fichiers.  
  
-   Effectuent des calculs de date et d'heure.  
  
-   Conservent plusieurs dates\/heures ayant un lien entre elles, comme les dates\/heures qui sont stockées sous la forme de deux valeurs distinctes ou de deux membres d'une structure.  
  
> [!NOTE]
>  Ces utilisations pour des valeurs <xref:System.DateTimeOffset> sont beaucoup plus courantes que celles pour les valeurs <xref:System.DateTime>. Par conséquent, <xref:System.DateTimeOffset> doit être considéré comme le type de date et d'heure par défaut pour le développement d'applications.  
  
 Une valeur <xref:System.DateTimeOffset> n'est pas liée à un fuseau horaire particulier, mais peut provenir de n'importe quel fuseau horaire. Pour illustrer cela, l'exemple suivant répertorie les fuseaux horaires auxquels plusieurs valeurs <xref:System.DateTimeOffset> \(y compris une Heure du Pacifique locale\) peuvent appartenir.  
  
 [!code-csharp[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual1.cs#1)]
 [!code-vb[System.DateTimeOffset.Conceptual#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual1.vb#1)]  
  
 La sortie montre que chaque valeur de date et d'heure de cet exemple peut appartenir à au moins trois fuseaux horaires différents. La valeur <xref:System.DateTimeOffset> de 6\/10\/2007 indique que si une valeur de date\/heure représente une heure d'été, son décalage avec le temps UTC ne correspond pas nécessairement au décalage UTC de base du fuseau horaire d'origine ou au décalage avec le temps UTC indiqué par son nom d'affichage. Cela signifie que, comme une valeur <xref:System.DateTimeOffset> n'est pas fortement couplée avec son fuseau horaire, elle ne peut pas refléter la transition d'un fuseau horaire vers et depuis l'heure d'été. Ceci peut être particulièrement problématique quand des calculs de date et d'heure sont utilisés pour manipuler une valeur <xref:System.DateTimeOffset>. \(Pour une présentation de la façon d’effectuer des calculs de date et d’heure en prenant en compte les règles d’ajustement d’un fuseau horaire, consultez [Exécution d'opérations arithmétiques avec des dates et heures](../../../docs/standard/datetime/performing-arithmetic-operations.md).\)  
  
## La structure TimeSpan  
 La structure <xref:System.TimeSpan> représente un intervalle de temps. Ses deux utilisations courantes sont :  
  
-   Refléter un intervalle de temps entre deux valeurs de date\/heure. Par exemple, la soustraction d'une valeur <xref:System.DateTime> d'une autre retourne une valeur <xref:System.TimeSpan>.  
  
-   Mesurer un temps écoulé. Par exemple, la propriété <xref:System.Diagnostics.Stopwatch.Elapsed%2A?displayProperty=fullName> retourne une valeur <xref:System.TimeSpan> qui reflète l'intervalle de temps écoulé depuis l'appel à une des méthodes <xref:System.Diagnostics.Stopwatch> qui commence à mesurer le temps écoulé.  
  
 Une valeur <xref:System.TimeSpan> peut également être utilisée en remplacement d'une valeur <xref:System.DateTime> quand cette valeur reflète un moment sans référence à une heure précise de la journée. Cette utilisation est similaire aux propriétés <xref:System.DateTime.TimeOfDay%2A?displayProperty=fullName> et <xref:System.DateTimeOffset.TimeOfDay%2A?displayProperty=fullName>, qui retournent une valeur <xref:System.TimeSpan> représentant l'heure sans référence à une date. Par exemple, la structure <xref:System.TimeSpan> peut être utilisée pour refléter les heures d'ouverture ou de fermeture quotidiennes d'un magasin, ou elle peut être utilisée pour représenter l'heure où se produit un événement régulier.  
  
 L'exemple suivant définit une structure `StoreInfo` qui inclut des objets <xref:System.TimeSpan> pour les heures d'ouverture et de fermeture d'un magasin, ainsi qu'un objet <xref:System.TimeZoneInfo> qui représente le fuseau horaire du magasin. La structure comprend également deux méthodes, `IsOpenNow` et `IsOpenAt`, qui indiquent si le magasin est ouvert à une heure spécifiée par l'utilisateur, qui est supposé être dans le fuseau horaire local.  
  
 [!code-csharp[Conceptual.ChoosingDates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#1)]
 [!code-vb[Conceptual.ChoosingDates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#1)]  
  
 La structure `StoreInfo` peut ensuite être utilisée par le code du client comme ce qui suit.  
  
 [!code-csharp[Conceptual.ChoosingDates#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.choosingdates/cs/datetimereplacement1.cs#2)]
 [!code-vb[Conceptual.ChoosingDates#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.choosingdates/vb/datetimereplacement1.vb#2)]  
  
## La classe TimeZoneInfo  
 La classe <xref:System.TimeZoneInfo> représente les fuseaux horaires de la terre et permet la conversion de toute date\/heure dans un fuseau horaire en son équivalent dans un autre fuseau horaire. La classe <xref:System.TimeZoneInfo> permet de travailler avec des dates et des heures de façon à ce qu'une valeur de date\/heure identifie d'une manière non ambiguë un point unique dans le temps. La classe <xref:System.TimeZoneInfo> est également extensible. Bien que dépendante des informations de fuseau horaire fournies pour les systèmes Windows et définies dans le Registre, elle prend en charge la création de fuseaux horaires personnalisés. Elle prend également en charge la sérialisation et la désérialisation des informations de fuseau horaire.  
  
 Dans certains cas, tirer parti de la classe <xref:System.TimeZoneInfo> peut nécessiter du travail de développement supplémentaire. Tout d'abord, les valeurs de date et d'heure ne sont pas étroitement couplées avec les fuseaux horaires auxquels elles appartiennent. Par conséquent, à moins que votre application ne fournisse un mécanisme permettant de lier une date\/heure avec son fuseau horaire associé, une valeur de date\/heure peut être facilement dissociée de son fuseau horaire. \(Une méthode pour lier ces informations consiste à définir une classe ou une structure qui contient à la fois la date\/heure et son objet de fuseau horaire associé\). Ensuite, Windows XP et les versions antérieures de Windows n'ont pas de véritable prise en charge de l'historique des informations de mesure de l'heure, et [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] n'en offre qu'une prise en charge limitée. Les applications qui sont conçues pour gérer des dates\/heures historiques doivent utilisent de façon intensive des fuseaux horaires personnalisés.  
  
 Tirer parti de la prise en charge des fuseaux horaires dans le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] est possible seulement si le fuseau horaire auquel appartient une valeur de date\/heure est connu quand cet objet de date\/heure est instancié. Ce n'est pas souvent le cas, en particulier dans les applications web ou réseau.  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)