---
title: "Vue d&#39;ensemble des fuseaux horaires | Microsoft Docs"
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
  - "règle d'ajustement (.NET Framework)"
  - "heure ambiguë (.NET Framework)"
  - "heure d'été (.NET Framework)"
  - "règle fixe (.NET Framework)"
  - "règle flottante (.NET Framework)"
  - "heure non valide (.NET Framework)"
  - "fuseaux horaires (.NET Framework), à propos des fuseaux horaires"
  - "fuseaux horaires (.NET Framework), créer"
  - "fuseaux horaires (.NET Framework), terminologie"
  - "TimeZoneInfo (classe), à propos de TimeZoneInfo (classe)"
  - "heure de transition (.NET Framework)"
ms.assetid: c4b7ed01-5e38-4959-a3b6-ef9765d6ccf1
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Vue d&#39;ensemble des fuseaux horaires
La classe <xref:System.TimeZoneInfo> simplifie la création d'applications prenant en charge les fuseaux horaires.  La classe <xref:System.TimeZone> prend en charge le fuseau horaire local et le temps universel coordonné \(UTC, Coordinated Universal Time\).  La classe <xref:System.TimeZoneInfo> prend en charge ces deux fuseaux horaires, ainsi que tous ceux pour lesquels des informations sont prédéfinies dans le Registre.  Vous pouvez également utiliser <xref:System.TimeZoneInfo> si vous souhaitez définir des fuseaux horaires personnalisés pour lesquels le système n'a pas d'informations.  
  
## Notions essentielles sur les fuseaux horaires  
 Un fuseau horaire est une zone géographique qui partage la même heure.  En général, mais pas toujours, les fuseaux horaires adjacents ont une heure de différence.  L'heure de chacun des fuseaux horaires du monde peut être exprimée comme un offset par rapport au temps universel coordonné.  
  
 De nombreux fuseaux horaires prennent en charge l'heure d'été.  L'heure d'été permet de profiter plus longtemps de la lumière du jour en avançant l'heure légale de 60 minutes au printemps ou au début de l'été. Le retour à l'heure normale \(ou heure d'hiver\) s'effectue à la fin de l'été ou en automne.  Ces modifications par rapport à l'heure d'hiver sont connues sous le nom de règles d'ajustement.  
  
 Le passage à\/de l'heure d'été dans un fuseau horaire donné peut être défini par une règle d'ajustement de date fixe ou flottante.  Une règle d'ajustement de date fixe définit une date particulière à laquelle le passage à\/de l'heure d'été se produit chaque année.  Par exemple, le passage de l'heure d'été à l'heure d'hiver qui a lieu chaque année le 25 octobre suit une règle d'ajustement de date fixe.  Les règles d'ajustement de date flottante sont beaucoup plus courantes. Elles définissent le jour d'une semaine d'un mois particulier pour le passage à\/de l'heure d'été.  Par exemple, le passage de l'heure d'hiver à l'heure d'été qui a lieu le troisième dimanche de mars suit une règle d'ajustement de date flottante.  
  
 Pour les fuseaux horaires qui prennent en charge des règles d'ajustement, le passage à\/de l'heure d'été crée deux types d'anomalies que sont les heures non valides et les heures ambiguës.  Une heure non valide est une heure inexistante créée par le passage de l'heure d'hiver à l'heure d'été.  Par exemple, si cette transition se produit un jour donné à 2h00 du matin et provoque l'heure de modification à 3h00 du matin, à chaque intervalle entre 2h00 du matin et 2h59 : 99 A.M valides.  Une heure ambiguë est une heure qui peut être mappée à deux heures différentes dans un fuseau horaire.  Elle résulte du passage de l'heure d'été à l'heure d'hiver.  Par exemple, si cette transition se produit un jour donné à 2h00 du matin et provoque l'heure de modification à 1h00 du matin, à chaque intervalle entre 1h00 du matin et 1h59 : 99 A.M peuvent être interprétées comme heure standard ou heure d'été.  
  
## Terminologie de fuseau horaire  
 Le tableau suivant définit les termes couramment utilisés lors de l'utilisation de fuseaux horaires et du développement d'applications prenant en charge les fuseaux horaires.  
  
|Terme|Définition|  
|-----------|----------------|  
|Règle d'ajustement|Règle qui définit quand a lieu le passage de l'heure d'hiver à l'heure d'été, et inversement.  Chaque règle d'ajustement comporte une date de début et une date de fin qui définissent sa période de validité \(par exemple, la règle d'ajustement commence le 1er janvier 1986 et se termine le 31 décembre 2006\), un delta \(différence exprimée en nombre d'heures par rapport à l'heure d'hiver, suite à l'application de la règle d'ajustement\) et des informations sur la date et l'heure spécifiques auxquelles doit avoir lieu le passage d'une heure à l'autre au cours de la période d'ajustement.  Le passage d'une heure à l'autre peut suivre la règle d'ajustement de date fixe ou la règle d'ajustement de date flottante.|  
|Heure ambiguë|Heure qui peut être mappée à deux heures différentes dans un fuseau horaire.  Cela se produit lorsque l'heure de l'horloge est reculée, comme lors du passage de l'heure d'été à l'heure d'hiver dans un fuseau horaire.  Par exemple, si cette transition se produit un jour donné à 2h00 du matin et provoque l'heure de modification à 1h00 du matin, à chaque intervalle entre 1h00 du matin et 1h59 : 99 A.M peuvent être interprétées comme heure standard ou heure d'été.|  
|Règle de date fixe|Règle d'ajustement qui définit une date particulière pour le passage à\/de l'heure d'été.  Par exemple, le passage de l'heure d'été à l'heure d'hiver qui a lieu chaque année le 25 octobre suit une règle d'ajustement de date fixe.|  
|Règle de date flottante|Règle d'ajustement qui définit le jour d'une semaine d'un mois particulier pour le passage à\/de l'heure d'été.  Par exemple, le passage de l'heure d'hiver à l'heure d'été qui a lieu le troisième dimanche de mars suit une règle d'ajustement de date flottante.|  
|Heure non valide|Heure inexistante qui est un artefact du passage de l'heure d'hiver à l'heure d'été.  Elle se produit lorsque l'heure de l'horloge est avancée, comme lors du passage de l'heure d'hiver à l'heure d'été dans un fuseau horaire.  Par exemple, si cette transition se produit un jour donné à 2h00 du matin et provoque l'heure de modification à 3h00 du matin, à chaque intervalle entre 2h00 du matin et 2h59 : 99 A.M valides.|  
|Heure de transition|Informations concernant un changement d'heure spécifique, tel que le passage de l'heure d'été à l'heure d'hiver ou vice versa, dans un fuseau horaire particulier.|  
  
## Fuseaux horaires et classe TimeZoneInfo  
 Dans le .NET Framework, un objet <xref:System.TimeZoneInfo> représente un fuseau horaire.  La classe <xref:System.TimeZoneInfo> inclut une méthode <xref:System.TimeZoneInfo.GetAdjustmentRules%2A> qui retourne un tableau d'objets <xref:System.TimeZoneInfo.AdjustmentRule>.  Chaque élément de ce tableau fournit des informations sur le passage à\/de l'heure d'été pour une période particulière \(pour les fuseaux horaires qui ne prennent pas en charge l'heure d'été, la méthode retourne un tableau vide\). Chaque objet <xref:System.TimeZoneInfo.AdjustmentRule> a une propriété <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A> et une propriété <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A> qui définissent la date et l'heure du passage à\/de l'heure d'été.  La propriété <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A> indique si ce passage est fixe ou flottant.  
  
 Le .NET Framework utilise les informations de fuseau horaire fournies par le système d'exploitation Windows et stockées dans le Registre.  Tous les fuseaux horaires existants ne sont pas représentés dans le Registre en raison du nombre important de fuseaux horaires dans le monde.  De plus, le Registre étant une structure dynamique, il est possible d'y ajouter les fuseaux horaires prédéfinis ou de les supprimer.  Enfin, le Registre ne contient pas nécessairement de données historiques sur les fuseaux horaires.  Par exemple, dans Windows XP, le Registre contient des données concernant un seul ensemble d'ajustements de fuseaux horaires.  Comme Windows Vista prend en charge des données dynamiques de fuseau horaire, un même fuseau horaire peut avoir plusieurs règles d'ajustement qui s'appliquent à des périodes spécifiques de plusieurs années.  Toutefois, la plupart des fuseaux horaires définis dans le Registre Windows Vista qui prennent en charge l'heure d'été ne comportent qu'une ou deux règles d'ajustement prédéfinies.  
  
 Comme la classe <xref:System.TimeZoneInfo> dépend du Registre, il n'est pas sûr qu'un fuseau horaire particulier soit défini dans le Registre en cas d'utilisation d'applications prenant en charge les fuseaux horaires.  Par conséquent, vous devez utiliser la gestion des exceptions lorsque vous essayez d'instancier un fuseau horaire spécifique \(autre que le fuseau horaire local ou le fuseau horaire représenté par l'heure UTC\).  L'exécution de l'application doit également pouvoir se poursuivre si un objet <xref:System.TimeZoneInfo> requis ne peut pas être instancié à partir du Registre.  
  
 Pour gérer l'absence d'un fuseau horaire requis, la classe <xref:System.TimeZoneInfo> inclut une méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> que vous pouvez utiliser pour créer des fuseaux horaires personnalisés introuvables dans le Registre.  Pour plus d'informations sur la création d'un fuseau horaire personnalisé, consultez [Comment : créer des fuseaux horaires sans règles d'ajustement](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) et [Comment : créer des fuseaux horaires avec des règles d'ajustement](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md).  En outre, vous pouvez faire appel à la méthode <xref:System.TimeZoneInfo.ToSerializedString%2A> pour convertir un nouveau fuseau horaire en une chaîne et l'enregistrer dans un magasin de données \(tel qu'une base de données, un fichier texte, le Registre ou une ressource d'application\).  Vous pouvez ensuite utiliser la méthode <xref:System.TimeZoneInfo.FromSerializedString%2A> pour reconvertir cette chaîne en un objet <xref:System.TimeZoneInfo>.  Pour plus d'informations, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) et [Comment : restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).  
  
 Chaque fuseau horaire étant caractérisé par un offset de base par rapport à l'heure UTC, ainsi que par un offset qui reflète toutes règles d'ajustement existantes, l'heure d'un fuseau horaire peut être facilement convertie dans un autre fuseau horaire.  À cette fin, l'objet <xref:System.TimeZoneInfo> inclut plusieurs méthodes de conversion, y compris :  
  
-   <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>qui convertit l'heure UTC en heure d'un fuseau horaire désigné.  
  
-   <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>qui convertit l'heure d'un fuseau horaire désigné en heure UTC.  
  
-   <xref:System.TimeZoneInfo.ConvertTime%2A> qui convertit l'heure d'un fuseau horaire désigné en heure d'un autre fuseau horaire désigné.  
  
-   <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> qui utilise des identificateurs de fuseau horaire \(au lieu d'objets <xref:System.TimeZoneInfo> \) comme paramètres de conversion de l'heure dans un fuseau horaire désigné en heure d'un autre fuseau horaire désigné.  
  
 Pour plus d'informations sur la conversion d'heures entre fuseaux horaires, consultez [Conversion d'heures entre fuseaux horaires](../../../docs/standard/datetime/converting-between-time-zones.md).  
  
## Voir aussi  
 [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)