---
title: "Utilisation de System.Transactions dans ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Utilisation de System.Transactions dans ASP.NET
Cette rubrique explique comment utiliser <xref:System.Transactions> dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
## Activation de DistributedTransactionPermission dans ASP.NET  
 <xref:System.Transactions> prend en charge les appelants d’un niveau de confiance partiel et est marqué avec l’attribut **AllowPartiallyTrustedCallers** \(APTCA\). Les niveaux de confiance pour les <xref:System.Transactions> sont définis d’après les types de ressource \(par exemple, la mémoire système, les ressources partagées au niveau du processus, les ressources système et d’autres ressources\) exposés par <xref:System.Transactions> et le niveau de confiance requis pour accéder à ces ressources. Dans un environnement de confiance partielle, un assembly qui n’a pas un niveau de confiance totale ne peut utiliser que les transactions du domaine d’application \(dans ce cas, les seules ressources protégées correspondent à la mémoire système\), sauf s’il dispose de l’autorisation <xref:System.Transactions.DistributedTransactionPermission>.  
  
 L’autorisation <xref:System.Transactions.DistributedTransactionPermission> est demandée chaque fois que la gestion des transactions est remontée pour être managée par le MSDTC \(Microsoft Distributed Transaction Coordinator\). Ce genre de scénario utilise des ressources au niveau du processus et, en particulier, une ressource globale servant d’espace réservé dans le journal MSDTC. Par exemple, le composant web frontal d’une base de données ou une application qui utilise une base de donnée en tant que partie des services qu’il fournit.  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dispose de son propre jeu de niveaux de confiance et associe un jeu d’autorisations spécifique à ces niveaux de confiance via des fichiers de stratégie.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [ASP.NET Trust Levels and Policy Files](../Topic/ASP.NET%20Trust%20Levels%20and%20Policy%20Files.md). Lors de la première installation du Kit de développement logiciel \(SDK\) Windows, aucun des fichiers de stratégie [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] par défaut n’est associé à <xref:System.Transactions.DistributedTransactionPermission>. Ainsi, lorsque votre transaction est remontée dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pour gestion par le MSDTC, la remontée échoue avec une <xref:System.Security.SecurityException> lors de la demande de <xref:System.Transactions.DistributedTransactionPermission>. Pour activer la remontée des transactions au sein d’un environnement [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de confiance partielle, vous devez accorder l’autorisation <xref:System.Transactions.DistributedTransactionPermission> aux mêmes niveaux de confiance par défaut que ceux de l’autorisation <xref:System.Data.SqlClient.SqlClientPermission>. Vous pouvez configurer vos propres niveaux de confiance et fichier de stratégie personnalisés pour la prise en charge ou modifier les fichiers de stratégie par défaut : **Web\_hightrust.config** et **Web\_mediumtrust.config**.  
  
 Pour modifier les fichiers de stratégie, ajoutez un élément **SecurityClass** pour **DistributedTransactionPermission** à l’élément **SecurityClasses** sous l’élément **PolicyLevel** et ajoutez un élément **IPermission** correspondant sous le [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** pour System.Transactions. Le fichier de configuration suivant illustre ceci.  
  
```  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] sur la stratégie de sécurité, consultez la page [securityPolicy élément \(Schéma des paramètres ASP.NET\)](http://msdn.microsoft.com/fr-fr/469d8d22-d263-46bb-8400-40d8d027faba).  
  
## Compilation dynamique  
 Pour importer et utiliser <xref:System.Transactions> dans une application [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] compilée dynamiquement lors de l’accès, insérez une référence à l’assembly <xref:System.Transactions> dans le fichier de configuration. Cette référence doit être ajoutée sous la section **compilation**\/**assemblies** du fichier de configuration **Web.config** racine par défaut ou du fichier de configuration d’une application Web spécifique. Cela est illustré par l'exemple suivant.  
  
```  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [add, élément de assemblies pour compilation \(Schéma des paramètres ASP.NET\)](http://msdn.microsoft.com/fr-fr/602197e8-108d-4249-b752-ba2a318f75e4).  
  
## Voir aussi  
 [ASP.NET Trust Levels and Policy Files](../Topic/ASP.NET%20Trust%20Levels%20and%20Policy%20Files.md)   
 [securityPolicy, élément \(Schéma des paramètres ASP.NET\)](http://msdn.microsoft.com/fr-fr/469d8d22-d263-46bb-8400-40d8d027faba)   
 [Remontée de la gestion des transactions ](../../../../docs/framework/data/transactions/transaction-management-escalation.md)