---
title: "Implement UI Automation Providers in a Client Application | Microsoft Docs"
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
  - "client-side UI Automation provider, implementation within applications"
  - "UI Automation, implementing client-side provider within application"
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
caps.latest.revision: 6
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 6
---
# Implement UI Automation Providers in a Client Application
> [!NOTE]
>  Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Cette rubrique contient un exemple de code qui montre comment implémenter un fournisseur UI Automation côté client dans une application.  
  
 Il s’agit d’un scénario rare. La plupart du temps, une application de client UI Automation utilise des fournisseurs côté serveur ou des fournisseurs côté client qui résident dans une DLL.  
  
## Exemple  
 L’exemple de code suivant implémente un fournisseur simple pour une fenêtre de console. Le code ne dispose pas de fonctionnalités utiles, mais il est destiné à présenter les étapes de base de l’installation d’un fournisseur dans le code client et de son inscription à l’aide de <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## Voir aussi  
 [UI Automation Providers Overview](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)   
 [Register a Client\-Side Provider Assembly](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)   
 [Create a Client\-Side UI Automation Provider](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)   
 [Client\-Side UI Automation Provider Implementation](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)