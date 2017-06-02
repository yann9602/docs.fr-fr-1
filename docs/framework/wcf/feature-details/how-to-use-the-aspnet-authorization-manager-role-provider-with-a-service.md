---
title: "Comment&#160;: utiliser le fournisseur de r&#244;le du Gestionnaire d&#39;autorisations ASP.NET avec un service | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Comment&#160;: utiliser le fournisseur de r&#244;le du Gestionnaire d&#39;autorisations ASP.NET avec un service
Lorsque [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] héberge un service Web, vous pouvez intégrer le Gestionnaire d'autorisations dans l'application pour fournir l'autorisation au service.  Le Gestionnaire d'autorisations permet à un développeur d'applications de définir des opérations individuelles qui peuvent être regroupées pour former des tâches.  Un administrateur peut autoriser ensuite que les rôles exécutent des tâches spécifiques ou des opérations individuelles.  Le Gestionnaire d'autorisations fournit un outil d'administration sous la forme d'un composant logiciel enfichable MMC \(Microsoft Management Console\) pour gérer des rôles, des tâches, des opérations et des utilisateurs.  Les administrateurs configurent un magasin de stratégie du Gestionnaire d'autorisations dans un fichier XML, Active Directory, ou dans un magasin Active Directory en mode application \(ADAM\).  
  
 Le Gestionnaire d'autorisations est intégré dans l'application en configurant le fournisseur de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] du Gestionnaire d'autorisations pour l'application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] qui héberge le service Web.  Comme les autres fournisseurs de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], le fournisseur de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] du Gestionnaire d'autorisations est configuré à l'aide de l'élément \<`providers`\>.  
  
 L'exemple de code suivant représente une partie d'un fichier de configuration pour un service Web qui intègre le Gestionnaire d'autorisations dans l'application.  
  
```  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"   
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'intégration d'un fournisseur de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] à une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation du Gestionnaire d'autorisations avec [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consultez [Comment : utiliser le Gestionnaire d'autorisations \(AzMan\) avec ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).  
  
## Voir aussi  
 [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)