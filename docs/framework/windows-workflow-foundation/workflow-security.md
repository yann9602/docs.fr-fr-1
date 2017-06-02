---
title: "S&#233;curit&#233; de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "programmation [WF], sécurité de workflow"
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# S&#233;curit&#233; de workflow
[!INCLUDE[wf](../../../includes/wf-md.md)] est intégré à plusieurs technologies différentes, telles que Microsoft SQL Server et [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  L'interaction avec ces technologies peut poser des problèmes de sécurité dans votre workflow si elle est effectuée de façon incorrecte.  
  
## Problèmes de sécurité de la persistance  
  
1.  Les flux de travail qui utilisent une activité <xref:System.Activities.Statements.Delay> et la persistance doivent être réactivés par un service.  Windows AppFabric utilise le service de gestion de flux de travail \(WMS\) pour réactiver les flux de travail dont les minuteurs ont expiré.  WMS crée un <xref:System.ServiceModel.WorkflowServiceHost> pour héberger le flux de travail réactivé.  Si le service WMS est arrêté, les workflows persistants ne seront pas réactivés à l'expiration de leurs minuteurs.  
  
2.  L'accès à l'instanciation durable doit être protégé contre les entités malveillantes externes au domaine d'application.  En outre, les développeurs doivent veiller à ce qu'il soit impossible d'exécuter du code malveillant dans le même domaine d'application que celui du code d'instanciation durable.  
  
3.  L'instanciation durable ne doit pas être exécutée avec des autorisations élevées \(administrateur\).  
  
4.  Les données traitées en dehors du domaine d'application doivent être protégées.  
  
5.  Les applications qui requièrent l'isolation de sécurité ne doivent pas partager la même instance d'abstraction de schéma.  De telles applications doivent utiliser des fournisseurs de magasins différents, ou enregistrer les fournisseurs configurés pour utiliser des instanciations différentes du magasin.  
  
## Problèmes de sécurité SQL Server  
  
-   Lors de l'utilisation d'un grand nombre d'activités enfants, d'emplacements, de signets, d'extensions hôtes ou d'étendues, ou de signets avec des charges utiles très importantes, la mémoire peut être épuisée ou des quantités inutiles d'espace de base de données peuvent être allouées pendant la persistance.  Cette situation peut être atténuée en utilisant la sécurité aux niveaux objet et base de données.  
  
-   Lors de l'utilisation de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, le magasin d'instances doit être sécurisé.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Méthodes pratiques pour SQL Server](http://go.microsoft.com/fwlink/?LinkId=164972).  
  
-   Les données sensibles dans le magasin d'instances doivent être chiffrées.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Chiffrement SQL Server](http://go.microsoft.com/fwlink/?LinkId=164976).  
  
-   Étant donné que la chaîne de connexion à une base de données est souvent incluse dans un fichier de configuration, la sécurité au niveau fenêtre \(ACL\) doit être utilisée pour vérifier que le fichier de configuration \(Web.Config généralement\) est sécurisé, et que les informations de connexion et de mot de passe ne sont pas incluses dans la chaîne de connexion.  L'authentification Windows doit être utilisée entre la base de données et le serveur Web à la place.  
  
## Considérations sur WorkflowServiceHost  
  
-   Les points de terminaison [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] utilisés dans les workflows doivent être sécurisés.  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Vue d'ensemble de la sécurité WCF](http://go.microsoft.com/fwlink/?LinkID=164975).  
  
-   L'autorisation au niveau hôte peut être implémentée à l'aide de <xref:System.ServiceModel.ServiceAuthorizationManager>.  Pour plus d'informations, consultez [Procédure : création d'un gestionnaire d'autorisations personnalisé pour un service](http://go.microsoft.com/fwlink/?LinkId=192228).  Cela est également illustré dans l'exemple suivant : [Sécurisation des services de workflow](../../../docs/framework/windows-workflow-foundation/samples/securing-workflow-services.md).  
  
-   Le ServiceSecurityContext pour le message entrant est également disponible dans le workflow en accédant à OperationContext.  Consultez [Accéder à un OperationContext à partir d'un service de workflow](../../../docs/framework/wcf/feature-details/accessing-operationcontext-from-a-workflow-service.md) pour plus de détails.  
  
## WF Security Pack CTP  
 Microsoft WF Security Pack CTP 1 est la première version préliminaire CTP \(Community Technology Preview\) d'un ensemble d'activités et de leur implémentation basée sur [Windows Workflow Foundation](http://msdn.microsoft.com/netframework/aa663328.aspx) dans [.NET Framework 4](http://msdn.microsoft.com/netframework/default.aspx) \(WF 4\) et [Windows Identity Foundation \(WIF\)](http://msdn.microsoft.com/security/aa570351.aspx).  Microsoft WF Security Pack CTP 1 contient les deux activités et leurs concepteurs qui expliquent comment vérifier facilement plusieurs scénarios liés à la sécurité en utilisant un workflow, notamment :  
  
1.  Emprunter l'identité d'un client dans le workflow  
  
2.  Autorisation dans\-le workflow, telle que PrincipalPermission et validation des revendications  
  
3.  Messagerie authentifiée en utilisant les ClientCredentials spécifiés dans le workflow, tels que le nom d'utilisateur\/mot de passe ou un jeton extrait d'un service d'émission de jeton de sécurité \(STS\)  
  
4.  Transfert d'un jeton de sécurité client vers un service principal \(délégation basée sur les revendications\) à l'aide de WS\-Trust ActAs  
  
 Pour plus d'informations et pour télécharger WF Security Pack CTP, consultez [WF Security Pack CTP](http://wf.codeplex.com/releases/view/48114).