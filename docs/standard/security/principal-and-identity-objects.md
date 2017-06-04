---
title: "Objets Principal et Identity | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GenericIdentity (objets)"
  - "GenericPrincipal (objets)"
  - "objets d'identité, à propos des objets d'identité"
  - "objets principaux, à propos des objets principaux"
  - "sécurité (.NET Framework), objets d'identité"
  - "sécurité (.NET Framework), principaux"
  - "WindowsIdentity (objets)"
  - "WindowsPrincipal (objets)"
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# Objets Principal et Identity
Un code managé peut découvrir l'identité ou le rôle d'une entité de sécurité par le biais d'un objet [Principal](frlrfSystemSecurityPrincipalIPrincipalClassTopic) ; ce dernier contient une référence à un objet [Identity](frlrfSystemSecurityPrincipalIIdentityClassTopic).  Il peut être utile d'établir un parallèle entre les objets Identity et Principal et des concepts plus familiers tels que les comptes d'utilisateurs et de groupes.  Dans la majorité des environnements de réseau, les comptes d'utilisateurs représentent des personnes ou des programmes, tandis que les comptes de groupes représentent diverses catégories d'utilisateurs et les droits qu'ils possèdent.  De la même façon, les objets Identity de .NET Framework représentent des utilisateurs tandis que les rôles correspondent à des appartenances et à des contextes de sécurité.  Dans .NET Framework, l'objet Principal encapsule à la fois un objet Identity et un rôle. Les applications .NET Framework octroient des droits à l'entité de sécurité en fonction de son identité ou, plus fréquemment, de son appartenance à un rôle.  
  
## Objets Identity  
 Un objet Identity encapsule des informations sur l'utilisateur ou sur l'entité en cours de validation.  À la base, les objets Identity contiennent un nom et un type d'authentification.  Le nom peut être celui d'un utilisateur ou d'un compte Windows, tandis que le type d'authentification peut être un protocole de connexion pris en charge, tel que Kerberos V5 ou une valeur personnalisée.  Le .NET Framework définit un objet <xref:System.Security.Principal.GenericIdentity> qui peut être utilisé pour la majorité des scénarios de connexion personnalisés et un objet <xref:System.Security.Principal.WindowsIdentity> plus spécifique que vous pouvez utiliser lorsque votre application doit avoir recours à l'authentification Windows.  En outre, vous pouvez définir votre propre classe d'identité qui encapsule des informations personnalisées sur les utilisateurs.  
  
 L'interface <xref:System.Security.Principal.IIdentity> définit les propriétés permettant d'accéder à un nom et à un type d'authentification, tel que Kerberos V5 ou NTLM.  Toutes les classes **Identity** implémentent l'interface **IIdentity**.  Aucune relation n'est obligatoire entre un objet **Identity** et le jeton de traitement Windows NT sous lequel un thread est actuellement exécuté.  Toutefois, si l'objet **Identity** est un objet **WindowsIdentity**, il est supposé que l'identité représente un jeton de sécurité Windows NT.  
  
## Objets Principal  
 L'objet principal représente le contexte de sécurité dans lequel le code est exécuté.  Les applications qui implémentent la sécurité basée sur les rôles accordent des droits en fonction du rôle associé à un objet Principal.  Comme les objets d'identité, le .NET Framework fournit un objet <xref:System.Security.Principal.GenericPrincipal> et un objet <xref:System.Security.Principal.WindowsPrincipal>.  Vous pouvez aussi définir des classes Principal personnalisées.  
  
 L'interface <xref:System.Security.Principal.IPrincipal> définit une propriété permettant d'accéder à un objet **Identity** associé, ainsi qu'une méthode permettant de déterminer si l'utilisateur identifié par l'objet **Principal** est membre d'un rôle donné.  Toutes les classes **Principal** implémentent l'interface **IPrincipal**, de même que toutes les autres propriétés et méthodes supplémentaires requises.  Par exemple, le Common Language Runtime fournit la classe **WindowsPrincipal** qui implémente des fonctionnalités supplémentaires pour le mappage à des rôles de l'appartenance à des groupes Windows NT ou Windows 2000.  
  
 Un objet **Principal** est lié à un objet de contexte d'appel \(<xref:System.Runtime.Remoting.Messaging.CallContext>\) dans un domaine d'application \(<xref:System.AppDomain>\).  Un contexte d'appel par défaut est toujours créé avec chaque nouveau **AppDomain** et il existe donc toujours un contexte d'appel en mesure d'accepter l'objet **Principal**.  Lorsqu'un nouveau thread est créé, un objet **CallContext** est également créé pour celui\-ci.  La référence de l'objet **Principal** est automatiquement copiée du thread en cours de création vers l'objet **CallContext** du nouveau thread.  Si le runtime n'est pas en mesure de déterminer l'objet **Principal** correspondant au créateur du thread, il se conforme à la stratégie par défaut applicable à la création des objets **Principal** et **Identity**.  
  
 Une stratégie paramétrable, propre au domaine d'application, définit les règles qui déterminent le type d'objet **Principal** à associer à un nouveau domaine d'application.  Si la stratégie de sécurité le permet, le runtime peut créer des objets **Principal** et **Identity** qui reflètent le jeton de système d'exploitation associé au thread d'exécution en cours.  Par défaut, le runtime utilise des objets **Principal** et **Identity** qui représentent des utilisateurs non authentifiés.  Ces objets **Principal** et **Identity** par défaut ne sont pas créés tant que le code ne tente pas d'y accéder.  
  
 Le code de confiance qui crée un domaine d'application peut définir la stratégie du domaine d'application qui gouverne la construction des objets **Principal** et **Identity** par défaut.  Cette stratégie spécifique au domaine d'application est applicable à tous les threads d'exécution dudit domaine d'application.  Un hôte de confiance non managé peut par nature définir cette stratégie. Toutefois, le code managé qui la définit doit disposer de la <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName> pour contrôler la stratégie de domaine.  
  
 Lors de la transmission d'un objet **Principal** vers plusieurs domaines d'application au cours d'un même traitement \(et donc sur le même ordinateur\), l'infrastructure de communication à distance copie une référence à l'objet **Principal** associé au contexte de l'appelant dans le contexte de l'appelé.  
  
## Voir aussi  
 [Comment : créer un objet WindowsPrincipal](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)   
 [Comment : créer des objets GenericPrincipal et GenericIdentity](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)   
 [Remplacement d'un objet Principal](../../../docs/standard/security/replacing-a-principal-object.md)   
 [Emprunt et restauration d'identité](../../../docs/standard/security/impersonating-and-reverting.md)   
 [Sécurité basée sur les rôles](../../../docs/standard/security/role-based-security.md)   
 [Concepts fondamentaux sur la sécurité](../../../docs/standard/security/key-security-concepts.md)