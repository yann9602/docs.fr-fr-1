---
title: "XAML Namespaces for .NET Framework XAML Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
caps.latest.revision: 3
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 3
---
# XAML Namespaces for .NET Framework XAML Services
Un espace de noms XAML est un concept qui se développe sur la définition d'un espace de noms XML.  De la même façon que pour un espace de noms XML, vous pouvez définir un espace de noms XAML via un attribut `xmlns` dans le balisage.  Les espaces de noms XAML sont également représentés dans le flux de nœud XAML et d'autres API de services XAML.  Cette rubrique traite le concept d'espace de noms XAML et explique comment les espaces de noms XAML peuvent être définis et sont utilisés par les contextes de schéma XAML et d'autres aspects des services XAML .NET Framework.  
  
## Espace de noms XML et espace de noms XAML  
 Un espace de noms XAML est un espace de noms XML spécialisé, tout comme XAML est une forme spécialisée de XML et utilise le formulaire XML de base pour son balisage.  Dans le balisage, vous déclarez un espace de noms XAML et son mappage via un attribut `xmlns` appliqué à un élément.  La déclaration `xmlns` peut être effectuée sur le même élément que l'espace de noms XAML.  Une déclaration d'espace de noms XAML adressée à un élément est valide pour cet élément, tous les attributs de cet élément, ainsi que tous les enfants de cet élément.  Les attributs peuvent utiliser des espaces de noms XAML différents de l'élément qui contient l'attribut, tant que le nom de l'attribut lui\-même fait référence au préfixe dans le cadre de son nom d'attribut dans le balisage.  
  
 La distinction entre un espace de noms XAML et un espace de noms XML est la suivante : ce dernier peut être utilisé pour référencer un schéma ou tout simplement pour différencier des entités.  Pour XAML, les types et les membres utilisés en XAML doivent correspondre aux types de stockage et les concepts de schéma XML ne s'appliquent pas bien à cette fonction.  L'espace de noms XAML contient des informations dont doit disposer le contexte de schéma XAML pour exécuter ce mappage de type.  
  
## Composants de l'espace de noms XAML  
 Par définition, l'espace de noms XAML possède deux composants : un préfixe et un identificateur.  Chacun de ces éléments est présent lorsqu'un espace de noms XAML est déclaré dans le balisage ou défini dans le système de type XAML.  
  
 Le préfixe peut être n'importe quelle chaîne autorisée par la [spécification des espaces de noms W3C dans XML 1.0](http://go.microsoft.com/fwlink/?LinkID=161735).  Par convention, les préfixes sont des chaînes généralement très courtes car le préfixe est répété à de nombreuses reprises dans un fichier de balisage classique.  Certains espaces de noms XAML conçus pour être utilisés dans des implémentations XAML multiples utilisent des préfixes classiques particuliers.  Exemple : l'espace de noms XAML du langage XAML est généralement mappé à l'aide du préfixe `x` Vous pouvez définir un espace de noms XAML par défaut, où le préfixe n'est pas donné dans la définition mais représenté en tant que chaîne vide s'il est défini ou interrogé par une API des services XAML .NET Framework.  En général, l'espace de noms XAML par défaut est délibérément sélectionné de façon à encourager une quantité maximum de balisage sans préfixe par une technologie XAML et ses scénarios et vocabulaires.  
  
 L'identificateur peut être n'importe quelle chaîne autorisée par la [spécification des espaces de noms W3C dans XML 1.0](http://go.microsoft.com/fwlink/?LinkID=161735).  Par convention, les identificateurs des espaces de noms XML ou XAML sont souvent donnés sous la forme d'URI, en général en tant qu'URI absolu à protocole.  Souvent, les informations de version qui définissent un vocabulaire XAML particulier sont implicites dans le cadre de la chaîne de chemin d'accès.  Les espaces de noms XAML ajoutent une convention d'identificateur supplémentaire au\-delà de la convention URI XML.  Pour les espaces de noms XAML, l'identificateur communique les informations qui sont requises par un contexte de schéma XAML pour résoudre les types spécifiés comme éléments dans cet espace de noms XAML ou faire correspondre des attributs à des membres.  
  
 Pour les besoins de la communication d'informations à un contexte de schéma XAML, l'identificateur d'un espace de noms XAML peut encore se trouver sous la forme d'URI.  Toutefois, dans ce cas, l'URI est également déclaré comme identificateur correspondant dans un assembly particulier ou une liste d'assemblys.  Cela s'effectue dans les assemblys en attribuant l'assembly doté de l'élément <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.  Cette méthode d'identification de l'espace de noms XAML et de prise en charge d'un comportement de résolution de type CLR dans l'assembly est pris en charge par le contexte de schéma XAML par défaut dans les services XAML de .NET Framework.  Plus généralement, cette convention peut être utilisée dans les cas où le contexte de schéma XAML incorpore le CLR ou se base sur le contexte de schéma XAML par défaut, requis pour pouvoir lire des attributs CLR d'assemblys CLR.  
  
 Les espaces de noms XAML peuvent également être identifiés par une convention communiquant un espace de noms CLR et un assembly de définition de type.  Cette convention est utilisée dans les cas où aucune attribution <xref:System.Windows.Markup.XmlnsDefinitionAttribute> n'existe dans les assemblys qui contiennent des types.  Cette convention est potentiellement plus complexe que la convention d'URI et présente également un potentiel d'ambiguïté et de duplication, étant donné qu'il existe de multiples façon de faire référence à un assembly.  
  
 La forme d'identificateur utilisant la convention d'espace de noms CLR et d'assembly la plus basique est la suivante :  
  
 `clr-namespace:` *NomClrns* `; assembly=` *NomCourtAssembly*  
  
 `clr-namespace:` et `; assembly=` sont des composants littéraux de la syntaxe.  
  
 *clrnsName* est le nom de chaîne qui identifie un espace de noms CLR.  Ce nom de chaîne inclut les caractères internes de points \(.\), qui fournissent des indication au sujet de l'espace de noms CLR et de sa relation à d'autres espaces de noms CLR.  
  
 *assemblyShortName* est le nom de chaîne d'un assembly qui définit les types utiles en XAML.  Les types auxquels il sera possible d'accéder via l'espace de noms XAML déclaré doivent être définis par l'assembly et spécifiquement déclarés dans l'espace de noms CLR spécifié par *clrnsName*.  Ce nom de chaîne met généralement en parallèle les informations rapportées par <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=fullName>.  
  
 Voici une définition plus exhaustive de la convention espace de noms CLR\/assembly :  
  
 `clr-namespace:` *NomClrns* `; assembly=` *NomAssembly*  
  
 *NomAssembly* représente toute chaîne autorisée en tant qu'entrée <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=fullName>.  Cette chaîne peut comprendre des informations de culture, de clé publique ou de version \(vous trouverez les définitions de ces concepts dans la rubrique de référence de <xref:System.Reflection.Assembly>\).  Le format et les preuves COFF \(utilisés par d'autres surcharges de<xref:System.Reflection.Assembly.Load%2A>\) ne sont pas appropriés pour le chargement d'assemblys XAML ; toutes les informations de chargement doivent être présentées sous forme de chaîne.  
  
 La spécification d'une clé publique pour l'assembly constitue une bonne technique en matière de sécurité XAML ou pour supprimer l'ambiguïté qui peut exister si les assemblys sont chargés par nom simple ou préexistent dans le cache ou le domaine d'application.  Pour plus d'informations, consultez [XAML Security Considerations](../../../docs/framework/xaml-services/xaml-security-considerations.md).  
  
## Déclarations d'espace de noms XAML dans l'API des services XAML  
 Dans l'API des services XAML, une déclaration d'espace de noms XAML est représentée par un objet <xref:System.Xaml.NamespaceDeclaration>.  Si vous déclarez un espace de noms XAML dans le code, vous appelez le constructeur <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29>.  Les paramètres `ns` et `prefix` sont spécifiés sous forme de chaînes et l'entrée à fournir pour ces paramètres correspond à la définition de l'identificateur de l'espace de noms XAML et au préfixe d'espace de noms XAML comme indiqués précédemment dans cette rubrique.  
  
 Si vous examinez les informations d'espace de noms XAML dans le cadre d'un flux de nœud XAML ou par un autre accès au système de type XAML, <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=fullName> renvoie l'identificateur d'espace de noms XAML et <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=fullName> le préfixe d'espace de noms XAML.  
  
 Dans un flux de nœud XAML, les informations d'espace de noms XAML peuvent apparaître sous la forme d'un nœud XAML précédent l'entité à laquelle il s'applique.  Cela comprend les cas où les informations d'espace de noms XAML précèdent l'élément `StartObject` de l'élément racine XAML.  Pour plus d'informations, consultez [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Dans de nombreux scénarios qui utilisent l'API des services XAML .NET Framework, au moins une déclaration d'espace de noms XAML doit exister, et cette déclaration doit contenir les informations requises par un contexte de schéma XAML ou y faire référence.  Les espaces de noms XAML doivent spécifier les assemblys à charger ou contribuer à résoudre des types spécifiques au sein des espaces de noms et assemblys déjà chargés ou connus par le contexte de schéma XAML.  
  
 Pour générer un flux de nœud XAML, les informations de type XAML doivent être disponibles par le biais du contexte de schéma XAML.  Pour pouvoir déterminer les informations de type XAML, il faut tout d'abord définir l'espace de noms XAML approprié pour chaque nœud à créer.  À ce stade, aucune instance de type n'est créée, mais le contexte de schéma XAML peut avoir besoin d'informations provenant de l'assembly de définition et du type de stockage.  Exemple : pour traiter l'élément `<Party><PartyFavor/></Party>` de balisage, le contexte de schéma XAML doit être en mesure de déterminer le nom et le type de l'élément `ContentProperty` de `Party` et a donc besoin des informations d'espace de noms XAML de `Party` et `PartyFavor`.  Dans le cas du contexte de schéma XAML par défaut, la réflexion statique rapporte une grande partie des informations système de type XAML requises pour générer des nœuds de type XAML dans le flux de nœud.  
  
 Pour générer un graphique d'objet à partir d'un flux de nœud XAML, des déclarations d'espace de noms XAML doivent exister pour chaque préfixe XAML utilisé dans le balisage d'origine et stocké dans le flux de nœud XAML.  À ce stade, les instances sont créées et le comportement de mappage de type commence véritablement.  
  
 Si vous voulez préremplir les informations d'espace de noms XAML, dans les cas où l'espace de noms XAML que vous voulez que le contexte de schéma XAML utilise n'est pas défini dans le balisage, vous pouvez utiliser des déclarations d'espace de noms XML <xref:System.Xml.XmlParserContext> pour un élément <xref:System.Xml.XmlReader>.  Utilisez alors cet élément <xref:System.Xml.XmlReader> comme entrée pour un constructeur de lecteur XAML ou <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=fullName>.  
  
 Deux autres API sont pertinentes en matière de gestion de l'espace de noms XAML dans les services XMAL de .NET Framework ; il s'agit de <xref:System.Windows.Markup.XmlnsDefinitionAttribute> et <xref:System.Windows.Markup.XmlnsPrefixAttribute>.  Ces attributs s'appliquent aux assemblys.  <xref:System.Windows.Markup.XmlnsDefinitionAttribute> est utilisé par un contexte de schéma XAML pour interpréter une déclaration d'espace de noms XAML incluant un URI.  <xref:System.Windows.Markup.XmlnsPrefixAttribute> est utilisé par les outils émettant du langage XAML afin qu'un espace de noms XAML particulier puisse être sérialisé avec un préfixe prédictible.  Pour plus d'informations, consultez [XAML\-Related CLR Attributes for Custom Types and Libraries](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## Voir aussi  
 [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)