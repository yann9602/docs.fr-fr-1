---
title: "DateTime, syntaxe XAML | Microsoft Docs"
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
  - "DateTime (syntaxe XAML) (WPF)"
  - "DateTime (syntaxe XAML) (WPF), chaînes de format pour"
  - "DateTime (syntaxe XAML) (WPF), chaînes pour"
  - "DateTime (syntaxe XAML) (WPF), cas d'utilisation"
  - "DateTime (texte XAML) (WPF)"
  - "format de date courte (WPF), DateTime"
ms.assetid: 5901710a-609b-40c8-9d65-f0016cd9090b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# DateTime, syntaxe XAML
Certains contrôles, tels que <xref:System.Windows.Controls.Calendar> et <xref:System.Windows.Controls.DatePicker>, possèdent des propriétés qui utilisent le type <xref:System.DateTime>.  Bien que l'on spécifie généralement une première date ou heure pour ces contrôles dans le code\-behind pendant l'exécution, vous pouvez spécifier une première date ou heure en XAML.  À la place, l'analyseur XAML WPF gère l'analyse des valeurs <xref:System.DateTime> à l'aide d'une syntaxe de texte XAML intégrée.  Cette rubrique décrit les caractéristiques de la syntaxe d'un texte XAML <xref:System.DateTime>  
  
   
  
<a name="where_datetime_xaml_syntax_is_used"></a>   
## Quand utiliser la syntaxe XAML DateTime  
 La définition des dates dans XAML n'est pas toujours nécessaire et peut même ne pas être souhaitable.  Par exemple, vous pouvez utiliser la propriété <xref:System.DateTime.Now%2A?displayProperty=fullName> pour initialiser une date pendant l'exécution ou vous pouvez effectuer tous les ajustements de date pour un calendrier dans le code\-behind en fonction de l'entrée utilisateur.  Toutefois, il existe des scénarios au cours desquels vous pouvez souhaiter coder en dur les dates dans <xref:System.Windows.Controls.Calendar> et <xref:System.Windows.Controls.DatePicker> dans un modèle de contrôle.  La syntaxe XAML de <xref:System.DateTime> doit être utilisée pour ces scénarios.  
  
### Date et heure de la syntaxe XAML est un comportement natif  
 <xref:System.DateTime> est une classe définie dans les bibliothèques de classes de base du CLR.  À cause de la façon dont les bibliothèques de classes de base sont en rapport avec le reste du CLR, il n'est pas possible d'appliquer <xref:System.ComponentModel.TypeConverterAttribute> à la classe et d'utiliser un convertisseur de type pour traiter des chaînes en XAML et les convertir en <xref:System.DateTime> dans le modèle objet au moment de l'exécution.  Il n'existe aucune classe `DateTimeConverter` qui fournisse le comportement de conversion ; le comportement de conversion décrit dans cette rubrique est natif à l'analyseur XAML WPF.  
  
<a name="format_strings_for_datetime_xaml_syntax"></a>   
## Chaînes de mise en forme pour la syntaxe XAML de DateTime  
 Vous pouvez spécifier le format d'un <xref:System.DateTime> avec une chaîne de format.  Les chaînes de mise en forme formalisent la syntaxe d'un texte qui peut être utilisée pour créer une valeur.  Les valeurs <xref:System.DateTime> des contrôles WPF existants utilisent en général uniquement les composants date de <xref:System.DateTime>, et pas les composants heure.  
  
 Lorsque vous spécifiez <xref:System.DateTime> en XAML, vous pouvez utiliser indifféremment chacune des chaînes de format.  
  
 Vous pouvez également utiliser des formats et des chaînes de mise en forme qui ne sont pas affichées spécifiquement dans cette rubrique.  Techniquement, le code XAML correspondant à toute valeur <xref:System.DateTime> qui est spécifiée, puis analysée par l'analyseur XAML WPF utilise un appel interne à <xref:System.DateTime.Parse%2A?displayProperty=fullName> ; par conséquent, vous pouvez employer toute chaîne acceptée par <xref:System.DateTime.Parse%2A?displayProperty=fullName> pour votre entrée XAML.  Pour plus d'informations, consultez <xref:System.DateTime.Parse%2A?displayProperty=fullName>.  
  
> [!IMPORTANT]
>  La syntaxe XAML de DateTime utilise toujours `en-us` comme <xref:System.Globalization.CultureInfo> pour sa conversion native.  Cela n'est pas influencé par la valeur <xref:System.Windows.FrameworkElement.Language%2A> ou la valeur `xml:lang` dans le code XAML, parce que la conversion de type de niveau d'attribut XAML agit sans ce contexte.  N'essayez pas d'interpoler les chaînes de mise en forme indiquées ici en raison de variations culturelles, telles que l'ordre dans lequel le jour et mois s'affichent.  Les chaînes de format présentées ici sont exactement celles qui sont utilisées lors de l'analyse du XAML, indépendamment des autres paramètres de culture.  
  
 Les sections suivantes décrivent certaines des chaînes de format <xref:System.DateTime> courantes.  
  
### Modèle de date courte \("d"\).  
 Ce qui suit affiche le format de date court pour un <xref:System.DateTime> en XAML :  
  
 `M/d/YYYY`  
  
 C'est la forme la plus simple qui spécifie toutes les informations nécessaires pour les utilisations typiques par les contrôles WPF, qui ne peut pas être influencée par des décalages de fuseau horaire accidentels par rapport à un composant « heure » et est recommandée par conséquent sur les autres formats.  
  
 Par exemple, pour spécifier la date du 1er juin 2010, utilisez la chaîne suivante :  
  
 `3/1/2010`  
  
 Pour plus d'informations, consultez <xref:System.Globalization.DateTimeFormatInfo.ShortDatePattern%2A?displayProperty=fullName>.  
  
### Modèle de date\/heure pouvant être trié \("s"\)  
 Ceci montre le modèle <xref:System.DateTime> triable en XAML :  
  
 `yyyy'-'MM'-'dd'T'HH':'mm':'ss`  
  
 Par exemple, pour spécifier la date du 1er juin 2010, utilisez la chaîne suivante \(les composants heure sont tous entrés comme 0\) :  
  
 `2010-06-01T000:00:00`  
  
### Modèle RFC1123 \("r"\)  
 Le modèle RFC1123 est utile car il peut s'agir d'une entrée de chaîne provenant d'autres générateurs de date qui utilisent également le modèle RFC1123 pour des raisons de culture indifférentes.  Ceci montre le modèle <xref:System.DateTime> RFC1123 en XAML :  
  
 `ddd, dd MMM yyyy HH':'mm':'ss 'UTC'`  
  
 Par exemple, pour spécifier la date du 1er juin 2010, utilisez la chaîne suivante \(les composants heure sont tous entrés comme 0\) :  
  
 `Mon, 01 Jun 2010 00:00:00 UTC`  
  
### Autres formats et modèles  
 Comme déclaré précédemment, un <xref:System.DateTime> en XAML peut être spécifié comme n'importe quelle chaîne qui est acceptable comme entrée pour <xref:System.DateTime.Parse%2A?displayProperty=fullName>.  Cela inclut d'autres formats formalisés \(par exemple <xref:System.Globalization.DateTimeFormatInfo.UniversalSortableDateTimePattern%2A>\) et des formats qui ne sont pas formalisés comme un formulaire <xref:System.Globalization.DateTimeFormatInfo> particulier.  Par exemple, la forme `YYYY/mm/dd` est acceptable comme entrée pour <xref:System.DateTime.Parse%2A?displayProperty=fullName>.  Cette rubrique n'essaie pas de décrire tous les formats possibles qui fonctionnent, mais recommande le modèle de date courte comme procédure habituelle.  
  
## Voir aussi  
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)