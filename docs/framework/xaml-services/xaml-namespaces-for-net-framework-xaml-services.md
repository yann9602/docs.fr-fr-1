---
title: Espaces de noms XAML pour les services XAML .NET Framework
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4e94f116fa820d80e5e23833c20382591c5d479
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>Espaces de noms XAML pour les services XAML .NET Framework
Un espace de noms XAML est un concept qui se développe sur la définition d’un espace de noms XML. Similaire à un espace de noms XML, vous pouvez définir un espace de noms XAML à l’aide un `xmlns` attribut dans le balisage. Espaces de noms XAML sont également représentées dans le flux de nœud XAML et d’autres API des Services XAML. Cette rubrique définit le concept d’espace de noms XAML et décrit comment les espaces de noms XAML peuvent être définis et utilisés par les contextes de schéma XAML et d’autres aspects des Services XAML .NET Framework.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Namespace XML et XAML Namespace  
 Un espace de noms XAML est un espace de noms XML spécialisé, tout comme XAML est une forme spécialisée de XML et utilise le formulaire XML de base pour son balisage. Dans le balisage, vous déclarez un espace de noms XAML et son mappage via un `xmlns` attribut appliqué à un élément. Le `xmlns` déclaration peut être faite au même élément déclaré dans l’espace de noms XAML. Une déclaration d’espace de noms XAML apportée à un élément est valide pour cet élément, tous les attributs de cet élément et tous les enfants de cet élément. Attributs peuvent utiliser des espaces de noms XAML qui n’est pas identique à l’élément qui contient l’attribut, tant que le nom d’attribut fait référence le préfixe dans le cadre de son nom d’attribut dans le balisage.  
  
 La différence d’un espace de noms XAML et un espace de noms XML est qu’un espace de noms XML peut être utilisé pour faire référence à un schéma, ou peut servir à différencier simplement les entités. Pour XAML, les types et membres utilisés en XAML doivent correspondre aux types de stockage et les concepts de schéma XML ne s’appliquent pas bien à cette fonction. L’espace de noms XAML contient des informations que le contexte de schéma XAML doit respecter les règles pour effectuer ce mappage de type.  
  
## <a name="xaml-namespace-components"></a>Composants de Namespace XAML  
 La définition d’espace de noms XAML comporte deux composants : un préfixe et un identificateur. Chacun de ces composants sont présents lorsqu’un espace de noms XAML est déclaré dans le balisage ou défini dans le système de type XAML.  
  
 Le préfixe peut être n’importe quelle chaîne autorisée par la [W3C des espaces de noms dans la spécification XML 1.0](http://go.microsoft.com/fwlink/?LinkID=161735) . Par convention, les préfixes sont des chaînes en général très courtes, car le préfixe est répété plusieurs fois dans un fichier de balisage standard. Certains espaces de noms XAML qui sont destinés à être utilisés dans plusieurs implémentations XAML utilisent des préfixes de conventionnelles particuliers. Par exemple, l’espace de noms XAML du langage XAML est généralement mappé à l’aide du préfixe `x`. Vous pouvez définir un espace de noms XAML par défaut, où le préfixe n’est pas spécifié dans la définition, mais est représenté comme une chaîne vide si défini ou interrogé by.NET Framework API des Services XAML. En règle générale, l’espace de noms XAML par défaut est délibérément choisi pour promouvoir une quantité maximum de sans préfixe balisage par une technologie XAML et ses scénarios et des vocabulaires.  
  
 L’identificateur peut être n’importe quelle chaîne autorisée par la [W3C des espaces de noms dans la spécification XML 1.0](http://go.microsoft.com/fwlink/?LinkID=161735). Par convention, identificateurs d’espaces de noms XML ou d’espaces de noms XAML sont souvent fournies sous forme d’URI, généralement sous la forme d’un URI absolu à protocole. Souvent, les informations de version qui définit un vocabulaire XAML particulier sont implicite dans le cadre de la chaîne de chemin d’accès. Ajouter des espaces de noms XAML une convention d’identificateur supplémentaire au-delà de la convention d’URI XML. Pour les espaces de noms XAML, l’identificateur communique les informations requises par un contexte de schéma XAML afin de résoudre les types qui sont spécifiés en tant qu’éléments sous cet espace de noms XAML, ou pour résoudre des attributs aux membres.  
  
 Pour des raisons de communiquer des informations à un contexte de schéma XAML, l’identificateur pour un espace de noms XAML peut-être toujours au format URI. Toutefois, dans ce cas l’URI est également déclaré comme un identificateur correspondant dans un assembly particulier ou une liste d’assemblys. Cette opération est effectuée dans les assemblys en attribuant l’assembly avec <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Cette méthode d’identification de l’espace de noms XAML et de prise en charge un comportement de résolution de type basé sur CLR dans l’assembly avec attributs est pris en charge par le contexte de schéma XAML par défaut dans les Services XAML .NET Framework. En règle générale, cette convention peut servir pour les cas où le contexte de schéma XAML incorpore le CLR ou qu’il est basé sur le contexte de schéma XAML par défaut, ce qui est nécessaire pour lire des attributs CLR à partir d’assemblys CLR.  
  
 Espaces de noms XAML peuvent également être identifiés par une convention qui communique un espace de noms CLR et un assembly de définition de type. Cette convention est utilisée dans les cas où aucun <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attribution existe dans les assemblys qui contiennent des types. Cette convention est potentiellement plus complexe que la convention d’URI et a également le potentiel d’ambiguïté et de duplication, car il existe plusieurs manières de faire référence à un assembly.  
  
 La forme la plus simple d’un identificateur qui utilise la convention d’espace de noms et d’assembly CLR est la suivante :  
  
 `clr-namespace:`*clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:`et `; assembly=` sont des composants littéraux de la syntaxe.  
  
 *clrnsName* est le nom de chaîne qui identifie un espace de noms CLR. Ce nom de chaîne inclut les caractères internes de points (.) qui fournissent des conseils sur l’espace de noms CLR et sa relation aux autres espaces de noms CLR.  
  
 *assemblyShortName* est le nom de chaîne d’un assembly qui définit les types qui sont utiles en XAML. Les types seront accessibles via l’espace de noms XAML déclaré sont censées être définis par l’assembly et spécifiquement déclarés dans l’espace de noms CLR spécifié par *clrnsName*. Ce nom de chaîne met généralement en parallèle les informations comme indiqué par <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Une définition plus complète de la convention d’espace de noms et d’assembly CLR est la suivante :  
  
 `clr-namespace:`*clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName* représente n’importe quelle chaîne pouvant être utilisé comme un <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> d’entrée. Cette chaîne peut inclure culture, clé publique ou les informations de version (définitions de ces concepts sont définies dans la rubrique de référence <xref:System.Reflection.Assembly>). COFF format et des preuves (utilisé par d’autres surcharges de <xref:System.Reflection.Assembly.Load%2A>) ne sont pas pertinentes pour XAML chargement d’assembly à des fins ; toutes les informations sur le chargement doivent être présentées sous forme de chaîne.  
  
 Spécification d’une clé publique pour l’assembly est une technique utile pour la sécurité XAML, ou pour supprimer l’ambiguïté qui peut exister si les assemblys sont chargés par nom simple ou existent déjà dans un domaine d’application ou du cache. Pour plus d’informations, consultez [considérations sur la sécurité XAML](../../../docs/framework/xaml-services/xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Déclarations de Namespace XAML dans l’API des Services XAML  
 Dans l’API des Services XAML, une déclaration d’espace de noms XAML est représentée par un <xref:System.Xaml.NamespaceDeclaration> objet. Si vous déclarez un espace de noms XAML dans le code, vous appelez le <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> constructeur. Le `ns` et `prefix` paramètres sont spécifiés sous forme de chaînes, et l’entrée à fournir pour ces paramètres correspond à la définition de l’identificateur d’espace de noms XAML et au préfixe d’espace de noms XAML, comme indiqué précédemment dans cette rubrique.  
  
 Si vous examinez les informations d’espace de noms XAML dans le cadre d’un flux de nœud XAML ou par un autre accès au système de type XAML, <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> signale l’identificateur d’espace de noms XAML, et <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> signale le préfixe d’espace de noms XAML.  
  
 Dans un flux de nœud XAML, les informations d’espace de noms XAML peuvent apparaître sous forme de nœud XAML qui précède l’entité à laquelle elle s’applique. Cela inclut les cas où les informations d’espace de noms XAML précédant le `StartObject` de l’élément racine XAML. Pour plus d'informations, consultez [Understanding XAML Node Stream Structures and Concepts](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Pour de nombreux scénarios qui utilisent les API des Services XAML .NET Framework, au moins une déclaration d’espace de noms XAML doit exister, et la déclaration doit contenir soit désignent les informations requises par un contexte de schéma XAML. Les espaces de noms XAML doivent spécifier les assemblys à charger, ou aider à résoudre des types spécifiques au sein d’espaces de noms et les assemblys qui sont déjà chargés ou connus par le contexte de schéma XAML.  
  
 Afin de générer un flux de nœud XAML, les informations de type XAML doivent être disponibles via le contexte de schéma XAML. Impossible de déterminer tout d’abord définir l’espace de noms XAML approprié pour chaque nœud créer les informations de type XAML. À ce stade, aucune instance de type n’est encore créé, mais le contexte de schéma XAML peut avoir besoin d’informations de l’assembly de définition et le type de sauvegarde. Par exemple, pour traiter le balisage `<Party><PartyFavor/></Party>`, le contexte de schéma XAML doit être en mesure de déterminer le nom et le type de la `ContentProperty` de `Party`et par conséquent doit également connaître les informations d’espace de noms XAML pour `Party` et `PartyFavor`. Dans le cas du contexte de schéma XAML par défaut, la réflexion statique rapporte une grande partie des informations système de type XAML sont nécessaire pour générer des nœuds de type XAML dans le flux de nœud.  
  
 Pour générer un graphique d’objet à partir d’un flux de nœud XAML, les déclarations d’espace de noms XAML doivent exister pour chaque préfixe XAML utilisé dans le balisage d’origine et enregistrée dans le flux de nœud XAML. À ce stade, instances sont en cours de création, et true-mappage de type de comportement se produit.  
  
 Si vous avez besoin préremplir les informations d’espace de noms XAML, dans les cas où l’espace de noms XAML que vous avez l’intention de contexte de schéma XAML à utiliser n’est pas défini dans le balisage, vous pouvez utiliser l’une des techniques consiste à déclarer les déclarations d’espace de noms XML dans le <xref:System.Xml.XmlParserContext> pour une <xref:System.Xml.XmlReader>. Utiliser ensuite <xref:System.Xml.XmlReader> en tant qu’entrée d’un constructeur de lecteur XAML, ou <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 Deux autres API qui sont pertinents pour la gestion des Services XAML .NET Framework de l’espace de noms XAML sont les attributs <xref:System.Windows.Markup.XmlnsDefinitionAttribute> et <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Ces attributs s’appliquent aux assemblys. <xref:System.Windows.Markup.XmlnsDefinitionAttribute>utilisé par un contexte de schéma XAML pour interpréter toute déclaration d’espace de noms XAML qui inclut un URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute>est utilisé par les outils émettant du langage XAML afin qu’un espace de noms XAML particulier peut être sérialisé avec un préfixe prédictible. Pour plus d’informations, consultez [Related les attributs CLR des Types personnalisés et des bibliothèques](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnement des concepts et structures du flux de nœud XAML](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
