---
title: "Vue d&#39;ensemble de la biblioth&#232;que de classes .NET Framework | Microsoft Docs"
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
  - ".NET Framework (bibliothèque de classes), à propos de"
  - ".NET Framework, bibliothèque de classes"
  - "types de base, bibliothèque de classes"
  - "types intégrés"
  - "bibliothèque de classes (.NET Framework)"
  - "objets de classe (type valeur)"
  - "classes (.NET Framework), bibliothèque (vue d'ensemble)"
  - "CLS"
  - "CLS (Common Language Specification)"
  - "types de données (.NET Framework)"
  - "types de données (.NET Framework), C#"
  - "types de données (.NET Framework), C++"
  - "types de données (.NET Framework), JScript"
  - "types de données (.NET Framework), Visual Basic"
  - "type valeur à virgule flottante"
  - "type valeur entier"
  - "JScript, types de données"
  - "bibliothèques, .NET Framework (bibliothèque de classes)"
  - "type valeur logique"
  - "membres (.NET Framework), type"
  - "espaces de noms (.NET Framework)"
  - "espaces de noms (.NET Framework), à propos des espaces de noms"
  - "conventions d'affectation de noms (.NET Framework)"
  - "System (espace de noms)"
  - "système de type (.NET Framework)"
  - "types, .NET Framework"
  - "types définis par l'utilisateur"
  - "types valeur"
  - "Visual Basic, types de données"
  - "Visual C#, types de données"
  - "Visual C++, types de données"
ms.assetid: 7e4c5921-955d-4b06-8709-101873acf157
caps.latest.revision: 19
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 19
---
# Vue d&#39;ensemble de la biblioth&#232;que de classes .NET Framework
Le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] inclut des classes, interfaces et types valeur qui permettent d'accélérer et d'optimiser le processus de développement et de fournir l'accès aux fonctions du système.  Pour faciliter l'interopérabilité entre les langages, la plupart des types .NET Framework sont conformes CLS \(Common Language Specification\) et peuvent, par conséquent, être utilisés à partir de n'importe quel langage de programmation dont le compilateur est conforme CLS.  
  
 Les types .NET Framework sont le fondement sur lequel les applications, composants et contrôles .NET sont construits.  Le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] comprend des types qui effectuent les fonctions suivantes :  
  
-   Représenter les types de données de base et les exceptions.  
  
-   Encapsuler les structures de données.  
  
-   Effectuer les E\/S.  
  
-   Accéder aux informations concernant les types chargés.  
  
-   Appeler les contrôles de sécurité .NET Framework.  
  
-   Fournir l'accès aux données, l'interface GUI riche côté client et l'interface GUI côté client contrôlée par le serveur.  
  
 Le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fournit un ensemble complet d'interfaces, ainsi que des classes abstraites et concrètes \(non abstraites\).  Vous pouvez utiliser les classes concrètes telles quelles ou, dans de nombreux cas, en dériver vos propres classes.  Pour utiliser les fonctionnalités d'une interface, vous pouvez créer une classe qui implémente l'interface ou dériver une classe d'une de celles du .NET Framework qui implémente l'interface.  
  
## Conventions d'affectation de noms  
 Les types .NET Framework utilisent un schéma d'affectation de noms dans lequel les points indiquent une hiérarchie.  Cette technique regroupe les types associés en espaces de noms de sorte qu'ils peuvent être recherchés et référencés plus facilement.  La première partie du nom complet \(jusqu'au point le plus à droite\) constitue le nom de l'espace de noms.  La dernière partie du nom est le nom du type.  Par exemple, **System.Collections.ArrayList** représente le type **ArrayList**, qui appartient à l'espace de noms **System.Collections**.  Les types qui se trouvent dans **System.Collections** peuvent être utilisés pour manipuler les collections d'objets.  
  
 Pour les développeurs de bibliothèques qui étendent le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], ce schéma d'affectation de noms facilite la création de groupes hiérarchiques de types et l'attribution d'un nom cohérent et descriptif.  Il permet également d'identifier clairement les types par leur nom complet \(autrement dit, par leur espace de noms et nom de type\) et d'empêcher les collisions de nom de type.  Les développeurs de bibliothèques sont censés utiliser la convention suivante lors de l'affectation de noms aux nouveaux espaces de noms :  
  
 *NomSociété*.*NomTechnologie*  
  
 Par exemple, l'espace de noms Microsoft.Word est conforme à cette indication.  
  
 L'utilisation de modèles d'affectation de noms pour regrouper des types associés en espaces de noms est très utile pour générer et documenter les bibliothèques de classes.  Cependant, ce schéma d'affectation de noms n'a pas d'effet sur la visibilité, l'accès aux membres, l'héritage, la sécurité ou la liaison.  Un espace de noms peut être partitionné en plusieurs assemblys et un seul assembly peut contenir des types provenant de plusieurs espaces de noms.  L'assembly fournit la structure formelle pour le versioning, le déploiement, la sécurité, le chargement et la visibilité dans le Common Language Runtime.  
  
 Pour plus d'informations sur les espaces de noms et les noms des types, consultez [Système de type commun \(CTS, Common Type System\)](../../docs/standard/base-types/common-type-system.md).  
  
## Espace de noms System  
 L'espace de noms <xref:System> est l'espace de noms racine pour les types fondamentaux du [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  Cet espace de noms comprend les classes qui représentent les types de données de base utilisés par toutes les applications : <xref:System.Object> \(racine de la hiérarchie d'héritage\), <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String>, et ainsi de suite.  Nombre de ces types correspondent aux types de données primitifs que votre langage de programmation utilise.  Lorsque vous écrivez du code à l'aide des types .NET Framework, vous pouvez utiliser le mot clé correspondant de votre langage lorsqu'un type de données de base .NET Framework est prévu.  
  
 Le tableau suivant énumère les types de base fournis par le [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], décrit brièvement chaque type et indique le type correspondant en Visual Basic, C\#, C\+\+ et JScript.  
  
|Catégorie|Nom de classe|Description|Type de données Visual Basic|Type de données C\#|Type de données C\+\+|Type de données JScript|  
|---------------|-------------------|-----------------|----------------------------------|-------------------------|---------------------------|-----------------------------|  
|Entier|<xref:System.Byte>|Entier non signé 8 bits.|**Byte**|**byte**|**unsigned char**|**Byte**|  
||<xref:System.SByte>|Entier signé 8 bits.<br /><br /> Non conforme CLS.|**SByte**|**sbyte**|**char**<br /><br /> ou<br /><br /> **signed** **char**|**SByte**|  
||<xref:System.Int16>|Entier signé 16 bits.|**Short**|**short**|**short**|**short**|  
||<xref:System.Int32>|Entier signe 32 bits.|**Entier**|**int**|**int**<br /><br /> ou<br /><br /> **long**|**int**|  
||<xref:System.Int64>|Entier signé 64 bits.|**Long**|**long**|**\_\_int64**|**long**|  
||<xref:System.UInt16>|Entier non signé 16 bits.<br /><br /> Non conforme CLS.|**UShort**|**ushort**|**unsigned short**|**UInt16**|  
||<xref:System.UInt32>|Entier non signé 32 bits.<br /><br /> Non conforme CLS.|**UInteger**|**uint**|**unsigned int**<br /><br /> ou<br /><br /> **unsigned long**|**UInt32**|  
||<xref:System.UInt64>|Entier non signé 64 bits.<br /><br /> Non conforme CLS.|**ULong**|**ulong**|**unsigned \_\_int64**|**UInt64**|  
|Virgule flottante|<xref:System.Single>|Nombre à virgule flottante \(32 bits\) simple précision.|**Single**|**float**|**float**|**float**|  
||<xref:System.Double>|Nombre à virgule flottante \(64 bits\) double précision.|**Double**|**double**|**double**|**double**|  
|Logique|<xref:System.Boolean>|Valeur booléenne \(true ou false\).|**Boolean**|**bool**|**bool**|**bool**|  
|Autre|<xref:System.Char>|Caractère Unicode \(16 bits\).|**Char**|**char**|**wchar\_t**|**char**|  
||<xref:System.Decimal>|Valeur décimale \(128 bits\).|**Decimal**|**decimal**|**Decimal**|**Decimal**|  
||<xref:System.IntPtr>|Entier signé dont la taille dépend de la plateforme sous\-jacente \(valeur 32 bits sur une plateforme 32 bits et valeur 64 bits sur une plateforme 64 bits\).|**IntPtr**<br /><br /> Pas de type intégré.|**IntPtr**<br /><br /> Pas de type intégré.|**IntPtr**<br /><br /> Pas de type intégré.|**IntPtr**|  
||<xref:System.UIntPtr>|Entier non signé dont la taille dépend de la plateforme sous\-jacente \(valeur 32 bits sur une plateforme 32 bits et valeur 64 bits sur une plateforme 64 bits\).<br /><br /> Non conforme CLS.|**UIntPtr**<br /><br /> Pas de type intégré.|**UIntPtr**<br /><br /> Pas de type intégré.|**UIntPtr**<br /><br /> Pas de type intégré.|**UIntPtr**|  
|Objets de classe|<xref:System.Object>|Racine de la hiérarchie d'objet.|**Objet**|**object**|**Object\***|**Objet**|  
||<xref:System.String>|Chaîne immuable à longueur fixe de caractères Unicode.|**String**|**string**|**String\***|**String**|  
  
 En plus des types de données de base, l'espace de noms <xref:System> contient plus de 100 classes, de celles qui gèrent les exceptions à celles qui traitent des principaux concepts relatifs au runtime, tels que les domaines d'application et le « garbage collector ».  L'espace de noms <xref:System> contient également de nombreux espaces de noms de deuxième niveau.  
  
 Pour plus d'informations sur les espaces de noms, consultez [Bibliothèque de classes .NET Framework](http://go.microsoft.com/fwlink/?LinkID=227195).  La documentation de référence fournit une vue d'ensemble de chaque espace de noms ainsi qu'une description formelle de chaque type et ses membres.  
  
## Voir aussi  
 [Système de type commun](../../docs/standard/base-types/common-type-system.md)   
 [Bibliothèque de classes .NET Framework](http://go.microsoft.com/fwlink/?LinkID=227195)   
 [Vue d'ensemble](../../docs/framework/get-started/overview.md)