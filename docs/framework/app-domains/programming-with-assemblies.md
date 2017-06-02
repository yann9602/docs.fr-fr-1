---
title: "Programmation &#224; l&#39;aide d&#39;assemblys | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "assemblys (.NET Framework), programmation"
  - "programmer des assemblys"
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# Programmation &#224; l&#39;aide d&#39;assemblys
Les assemblys sont les blocs de constructions du .NET Framework ; ils constituent l'unité fondamentale de déploiement, contrôle de version, réutilisation, portée de l'activation et autorisation de sécurité.  Un assembly fournit au Common Language Runtime les informations dont il a besoin pour reconnaître les implémentations des types.  Il s'agit d'une collection de types et de ressources générées pour fonctionner ensemble et former une unité logique de fonctionnalité.  Pour le runtime, un type n'existe pas en dehors du contexte d'un assembly.  
  
 Cette section explique comment créer des modules, créer des assemblys à partir de modules, créer une paire de clés et signer un assembly avec un nom fort et installer un assembly dans le Global Assembly Cache.  Cette section explique également comment utiliser le [Désassembleur MSIL \(Ildasm.exe\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour visualiser les informations du manifeste d'assembly.  
  
> [!NOTE]
>  Démarrant avec le .NET Framework version 2.0, le runtime ne chargera pas un assembly qui a été compilé avec une version du .NET Framework dont le numéro de version est plus élevé que le runtime actuellement chargé.  Cela s'applique à la combinaison des composants majeurs et mineurs du numéro de version.  
  
## Dans cette section  
 [Création d'assemblys](../../../docs/framework/app-domains/create-assemblies.md)  
 Fournit une vue d'ensemble des assemblys multifichiers et à fichier unique.  
  
 [Noms d'assemblys](../../../docs/framework/app-domains/assembly-names.md)  
 Fournit une vue d'ensemble de l'affectation de noms aux assemblys.  
  
 [Comment : déterminer le nom qualifié complet d'un assembly](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Explique comment déterminer le nom qualifié complet d'un assembly.  
  
 [Exécution d'applications intranet de confiance totale](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Explique comment spécifier une stratégie de sécurité héritée pour les assemblys de confiance totale sur un partage intranet.  
  
 [Emplacement de l'assembly](../../../docs/framework/app-domains/assembly-location.md)  
 Fournit une vue d'ensemble sur l'emplacement des assemblys.  
  
 [Comment : générer un assembly à fichier unique](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Explique comment créer un assembly à fichier unique.  
  
 [Assemblys multifichiers](../../../docs/framework/app-domains/multifile-assemblies.md)  
 Présente les raisons justifiant la création d'assemblys multifichiers.  
  
 [Comment : générer un assembly multifichier](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Explique comment créer un assembly multifichier.  
  
 [Définition des attributs d'assembly](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Décrit les attributs d'assembly et la façon de les définir.  
  
 [Création et utilisation d'assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 Explique comment et pourquoi signer un assembly avec un nom fort, et comporte des rubriques "Comment".  
  
 [Temporisation de signature d'un assembly](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Explique comment différer la signature d'un assembly.  
  
 [Utilisation d'assemblys et du Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Explique comment et pourquoi ajouter des assemblys au Global Assembly Cache, et comporte des rubriques "Comment".  
  
 [Comment : afficher le contenu d'un assembly](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Explique comment utiliser le Désassembleur MSIL \(Ildasm.exe\) pour visualiser le contenu des assemblys.  
  
 [Transfert de type dans le Common Language Runtime](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Décrit comment utiliser le transfert de type pour déplacer un type dans un assembly différent sans interrompre les applications existantes.  
  
## Référence  
 <xref:System.Reflection.Assembly>  
 Classe .NET Framework qui représente un assembly.  
  
## Rubriques connexes  
 [Comment : obtenir des informations relatives au type et aux membres à partir d'un assembly](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Explique comment obtenir par programme des informations, notamment sur les types, à partir d'un assembly.  
  
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Fournit une vue d'ensemble conceptuelle des assemblys du Common Language Runtime.  
  
 [Versioning des assemblys](../../../docs/framework/app-domains/assembly-versioning.md)  
 Propose une vue d'ensemble de la liaison d'assemblys et des attributs <xref:System.Reflection.AssemblyVersionAttribute> et <xref:System.Reflection.AssemblyInformationalVersionAttribute>.  
  
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Explique comment le runtime détermine quel assembly utiliser pour répondre à une demande de liaison.  
  
 [Réflexion](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.