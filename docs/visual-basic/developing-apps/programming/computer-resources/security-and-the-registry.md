---
title: "Security and the Registry (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "security [Visual Basic], registry"
  - "registry, security issues"
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Security and the Registry (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette page discute des conséquences pour la sécurité liées au stockage de données dans le Registre.  
  
## Autorisations  
 Pour des raisons de sécurité, il est déconseillé de stocker des données confidentielles, telles que des mots de passe, en texte brut dans le Registre, même si la clé de Registre est protégée par des listes de contrôle d'accès \(ACL, Access Control Lists\).  
  
 L'utilisation du Registre peut compromettre la sécurité par l'accord d'accès inappropriés aux ressources du système ou aux informations protégées.  Pour utiliser ces propriétés, vous devez posséder des autorisations de lecture et d'écriture de l'énumération <xref:System.Security.Permissions.RegistryPermissionAccess>, qui contrôle l'accès aux variables de Registre.  Tout code s'exécutant avec une confiance totale \(dans la stratégie de sécurité par défaut, tout code installé sur le disque dur local de l'utilisateur\) détient les autorisations nécessaires pour accéder au Registre.  Pour plus d'informations, consultez la classe <xref:System.Security.Permissions.RegistryPermission>.  
  
 Les variables de Registre ne doivent pas être stockées dans des emplacements de mémoire où elles sont accessibles à du code sans <xref:System.Security.Permissions.RegistryPermission>.  De même, lorsque vous accordez des autorisations, accordez les privilèges minimaux nécessaires pour effectuer le travail.  
  
 Les valeurs d'accès de l'autorisation Registre sont définies par l'énumération <xref:System.Security.Permissions.RegistryPermissionAccess>.  Le tableau suivant décrit en détail ses membres.  
  
|Valeur|Accès aux variables de Registre|  
|------------|-------------------------------------|  
|`AllAccess`|Création, lecture et écriture|  
|`Create`|Créer|  
|`NoAccess`|Pas d'accès|  
|`Read`|Lecture|  
|`Write`|Écrire|  
  
## Vérification des valeurs dans les clés de Registre  
 Lorsque vous créez une valeur de Registre, vous devez déterminer la marche à suivre si cette valeur existe déjà.  Il est possible qu'un autre processus, peut\-être nuisible, ait déjà créé la valeur et puisse y accéder.  Lorsque vous placez des données dans la valeur du Registre, elles sont disponibles pour les autres processus.  Pour empêcher cela, utilisez la méthode `GetValue`.  Elle retourne `Nothing` si la clé n'existe pas.  
  
> [!IMPORTANT]
>  Lors de la lecture du Registre à partir d'une application Web, l'identité de l'utilisateur actuel dépend de l'authentification et de l'emprunt d'identité implémentés dans l'application Web.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 [Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)