---
title: "Comment&#160;: restreindre l&#39;acc&#232;s &#224; l&#39;aide de la classe PrincipalPermissionAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "PrincipalPermissionAttribute (classe)"
  - "WCF, autorisation"
  - "WCF, sécurité"
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# Comment&#160;: restreindre l&#39;acc&#232;s &#224; l&#39;aide de la classe PrincipalPermissionAttribute
Le contrôle de l'accès aux ressources sur un ordinateur de domaine Windows est une tâche de sécurité de base.Par exemple, certains utilisateurs doivent pouvoir consulter des données sensibles, telles que les informations relatives aux salaires.Cette rubrique explique comment restreindre l'accès à une méthode en exigeant que l'utilisateur appartienne à un groupe prédéfini.Pour obtenir un exemple fonctionnel, consultez [Authorizing Access to Service Operations](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 La tâche se compose de deux procédures séparées.La première crée le groupe et le remplit avec les utilisateurs.La deuxième applique la classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> pour spécifier le groupe.  
  
### Pour créer un groupe Windows  
  
1.  Ouvrez la console **Gestion de l'ordinateur**.  
  
2.  Dans le panneau gauche, cliquez sur **Utilisateurs et groupes locaux**.  
  
3.  Cliquez avec le bouton droit sur **Groupes**, puis sur **Nouveau groupe**.  
  
4.  Dans la zone **Nom du groupe**, tapez un nom pour le nouveau groupe.  
  
5.  Dans la zone **Description**, tapez une description du nouveau groupe.  
  
6.  Pour ajouter de nouveaux membres au groupe, cliquez sur **Ajouter**.  
  
7.  Si vous vous êtes vous\-même ajouté au groupe et souhaitez tester le code suivant, vous devez vous déconnecter, puis vous reconnecter à l'ordinateur pour être inclus dans le groupe.  
  
### Pour demander l'appartenance des utilisateurs  
  
1.  Ouvrez le fichier de code [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] qui contient le code de contrat de service implémenté.[!INCLUDE[crabout](../../../includes/crabout-md.md)] l'implémentation d'un contrat, consultez [Implémentation de contrats de service](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2.  Appliquez l'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> à chaque méthode qui doit être restreinte à un groupe spécifique.Affectez <xref:System.Security.Permissions.SecurityAction> à la propriété <xref:System.Security.Permissions.SecurityAttribute.Action%2A> et le nom du groupe à la propriété <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>.Par exemple :  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  Si vous appliquez l'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> à un contrat, une exception <xref:System.Security.SecurityException> sera levée.Vous pouvez appliquer l'attribut uniquement au niveau de la méthode.  
  
## Utilisation d'un certificat pour contrôler l'accès à une méthode  
 Vous pouvez également utiliser la classe `PrincipalPermissionAttribute` pour contrôler l'accès à une méthode si le type d'informations d'identification du client est un certificat.Pour ce faire, vous devez avoir l'empreinte numérique et le sujet du certificat.  
  
 Pour examiner les propriétés d'un certificat, consultez [Comment : afficher des certificats à l'aide du composant logiciel enfichable MMC](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).Pour rechercher la valeur d'empreinte numérique, consultez [Comment : récupérer l'empreinte numérique d'un certificat](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### Pour contrôler l'accès à l'aide d'un certificat  
  
1.  Appliquez la classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> à la méthode à laquelle vous souhaitez restreindre l'accès.  
  
2.  Affectez <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> à l'action de l'attribut.  
  
3.  Affectez à la propriété `Name` une chaîne qui se compose du nom du sujet et de l'empreinte numérique du certificat.Séparez les deux valeurs par un point\-virgule et un espace, tel qu'indiqué dans l'exemple suivant :  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  Affectez <xref:System.ServiceModel.Description.PrincipalPermissionMode> à la propriété <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A>, tel qu'indiqué dans l'exemple de configuration suivant :  
  
    ```  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     L'affectation de `UseAspNetRoles` à cette valeur indique que la propriété `Name` de `PrincipalPermissionAttribute` sera utilisée pour effectuer une comparaison de chaînes.Lorsqu'un certificat est utilisé en tant qu'information d'identification du client, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] concatène par défaut l'empreinte numérique et le nom commun du certificat à un point\-virgule pour créer une valeur unique pour l'identité principale du client.Avec `UseAspNetRoles` défini en tant que `PrincipalPermissionMode` sur le service, la valeur de cette identité principale est comparée à celle de la propriété `Name` afin de déterminer les droits d'accès de l'utilisateur.  
  
     Vous pouvez également, lorsque vous créez un service auto\-hébergé, définir la propriété <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> dans le code, tel qu'indiqué dans le code suivant :  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## Voir aussi  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>   
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>   
 <xref:System.Security.Permissions.SecurityAction>   
 <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>   
 [Authorizing Access to Service Operations](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)   
 [Vue d'ensemble de la sécurité](../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Implémentation de contrats de service](../../../docs/framework/wcf/implementing-service-contracts.md)