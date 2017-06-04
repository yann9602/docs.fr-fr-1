---
title: "Comment&#160;: impl&#233;menter la connexion utilisateur avec les services d&#39;application cliente | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services d'application cliente, authentifier les utilisateurs"
  - "valider les utilisateurs (services d'application cliente)"
  - "validation (.NET Framework), services d'application cliente"
ms.assetid: 5431a671-eb02-4e18-a651-24764fccec9a
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: impl&#233;menter la connexion utilisateur avec les services d&#39;application cliente
Vous pouvez utiliser les services d'application cliente pour valider des utilisateurs via un service de profil [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] existant.  Pour plus d'informations sur la façon de configurer le service de profil [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)], consultez [Using Forms Authentication with Microsoft Ajax](../Topic/Using%20Forms%20Authentication%20with%20Microsoft%20Ajax.md).  
  
 Les procédures suivantes décrivent comment valider des utilisateurs par le biais du service d'authentification lorsque votre application est configurée pour utiliser l'un des fournisseurs de services d'authentification du client.  Pour plus d'informations, consultez [Comment : configurer les services d'application cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
 En général, vous exécutez l'ensemble de la validation via la méthode `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName>.  Cette méthode gère l'interaction avec le service d'authentification par le biais du fournisseur d'authentification configuré.  Pour plus d'informations, consultez [Vue d'ensemble des services d'application cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
 Les procédures d'authentification par formulaire requièrent l'accès à un service d'authentification [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] en cours d'exécution.  Pour obtenir des instructions sur le test complet des fonctionnalités des services d'application cliente, consultez [Procédure pas à pas : utilisation des services d'application cliente](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
### Pour authentifier un utilisateur avec l'authentification par formulaire à l'aide d'un fournisseur d'informations d'identification d'appartenance  
  
1.  Implémentez l'interface <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>.  L'exemple de code suivant indique une implémentation <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=fullName> d'une classe de boîte de dialogue de connexion dérivée de <xref:System.Windows.Forms.Form?displayProperty=fullName>.  Cette boîte de dialogue contient des zones de texte pour le nom d'utilisateur et le mot de passe, ainsi qu'une case à cocher « Mémoriser le mot de passe ».  Lorsque le fournisseur d'authentification du client appelle la méthode <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A>, le formulaire s'affiche.  Lorsque l'utilisateur fournit les informations dans la boîte de dialogue de connexion et clique sur OK, les valeurs spécifiées sont retournées dans un nouvel objet <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>.  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]
     [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  Appelez la méthode `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> et passez des chaînes vides comme valeurs de paramètre.  Lorsque vous spécifiez des chaînes vides, cette méthode appelle en interne la méthode <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> pour le fournisseur d'informations d'identification configuré pour votre application.  L'exemple de code suivant appelle cette méthode pour restreindre l'accès à une application Windows Forms tout entière.  Vous pouvez ajouter ce code à un gestionnaire <xref:System.Windows.Forms.Form.Load?displayProperty=fullName>.  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]
     [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### Pour authentifier un utilisateur avec l'authentification par formulaire sans utiliser un fournisseur d'informations d'identification d'appartenance  
  
-   Appelez la méthode `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> et passez les valeurs de nom d'utilisateur et de mot de passe récupérées à partir de l'utilisateur.  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]
     [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### Pour authentifier un utilisateur avec l'authentification Windows  
  
-   Appelez la méthode `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> et passez des chaînes vides pour les paramètres.  Cet appel de méthode retourne toujours la valeur `true` et ajoute un cookie au cache de cookie de l'utilisateur qui contient l'identité Windows.  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]
     [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## Programmation fiable  
 L'exemple de code présenté dans cette rubrique montre les utilisations les plus simples de l'authentification dans une application cliente Windows.  Toutefois, lorsque vous appelez la méthode `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=fullName> avec les services d'application cliente et l'authentification par formulaire, votre code peut lever une <xref:System.Net.WebException>.  Cela indique que le service d'authentification n'est pas disponible.  Pour obtenir un exemple illustrant la gestion de cette exception, consultez [Procédure pas à pas : utilisation des services d'application cliente](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
## Voir aussi  
 [Services d'application cliente](../../../docs/framework/common-client-technologies/client-application-services.md)   
 [Vue d'ensemble des services d'application cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md)   
 [Comment : configurer les services d'application cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)   
 [Procédure pas à pas : utilisation des services d'application cliente](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)   
 [Using Forms Authentication with Microsoft Ajax](../Topic/Using%20Forms%20Authentication%20with%20Microsoft%20Ajax.md)