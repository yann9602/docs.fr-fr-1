---
title: "Comment&#160;: cr&#233;er une strat&#233;gie d&#39;autorisation personnalis&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er une strat&#233;gie d&#39;autorisation personnalis&#233;e
L'infrastructure de modèle d'identité dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] prend en charge un modèle d'autorisation basé sur les revendications.Les revendications, une fois extraites des jetons, sont traitées par une stratégie d'autorisation personnalisée lorsqu'une telle stratégie a été définie, puis placées dans un <xref:System.IdentityModel.Policy.AuthorizationContext>, lequel peut ensuite être examiné afin de délivrer ou non les autorisations.Il est possible d'utiliser une stratégie personnalisée afin de transformer les revendications émanant des jetons entrants en revendications escomptées par l'application.De cette façon, les détails des différentes revendications provenant des différents types de jetons pris en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont épargnés à l'application.Cette rubrique contient des instructions permettant d'implémenter une stratégie d'autorisation personnalisée et d'ajouter celle\-ci à la collection de stratégies utilisées par un service donné.  
  
### Pour implémenter une stratégie d'autorisation personnalisée  
  
1.  Définissez une nouvelle classe dérivée de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Implémentez la propriété <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> en lecture seule en générant une chaîne unique dans le constructeur de la classe et en faisant en sorte que cette chaîne soit retournée à chaque accès à la propriété.  
  
3.  Implémentez la propriété <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> en lecture seule en retournant un <xref:System.IdentityModel.Claims.ClaimSet> qui représente l'émetteur de la stratégie.Il peut s'agir d'un `ClaimSet` qui représente l'application ou d'un `ClaimSet` intégré \(par exemple, le `ClaimSet` retourné par la propriété <xref:System.IdentityModel.Claims.ClaimSet.System%2A> statique\).  
  
4.  Implémentez la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> comme décrit dans la procédure suivante.  
  
### Pour implémenter la méthode d'évaluation  
  
1.  Deux paramètres sont passés à cette méthode : une instance de la classe <xref:System.IdentityModel.Policy.EvaluationContext> ainsi qu'une référence d'objet.  
  
2.  Si la stratégie d'autorisation personnalisée ajoute des instances <xref:System.IdentityModel.Claims.ClaimSet> indépendamment du contenu actuel du <xref:System.IdentityModel.Policy.EvaluationContext>, ajoutez alors chaque `ClaimSet` en appelant la méthode <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29>, puis retournez la valeur `true` depuis la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A>.Le renvoi de la valeur `true` indique à l'infrastructure d'autorisation que la stratégie d'autorisation a terminé son travail et qu'il n'est plus nécessaire de l'appeler.  
  
3.  Si la stratégie d'autorisation personnalisée ajoute des ensembles de revendications uniquement lorsque des revendications sont déjà présentes dans le `EvaluationContext`, recherchez ces revendications en examinant les instances `ClaimSet` retournées par la propriété <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A>.Si des revendications sont déjà présentes, ajoutez les nouveaux ensembles de revendications en appelant la méthode <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29>, puis, lorsqu'il n'y a plus d'ensembles de revendications à ajouter, retournez la valeur `true` afin d'indiquer à l'infrastructure d'autorisation que la stratégie d'autorisation a terminé son travail.En l'absence de revendications, retournez la valeur `false` afin d'indiquer que la stratégie d'autorisation doit encore être appelée lorsque d'autres stratégies d'autorisation souhaitent ajouter de nouveaux ensembles de revendications au `EvaluationContext`.  
  
4.  Lorsque les autorisations nécessitent un traitement plus complexe, notamment une évaluation particulière, le second paramètre de la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> est utilisé pour stocker une variable d'état que l'infrastructure d'autorisation repasse à chaque nouvel appel de la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29>.  
  
### Pour spécifier une stratégie d'autorisation personnalisée dans le fichier de configuration  
  
1.  Spécifiez le type de la stratégie d'autorisation personnalisée dans l'attribut `policyType` de l'élément `add` de l'élément `authorizationPolicies` de l'élément `serviceAuthorization`.  
  
    ```  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>         
            <add policyType="Samples.MyAuthorizationPolicy"  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### Pour spécifier une stratégie d'autorisation personnalisée dans le code  
  
1.  Créez une liste <xref:System.Collections.Generic.List%601> de <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.  
  
2.  Créez une instance de la stratégie d'autorisation personnalisée.  
  
3.  Ajoutez l'instance de la stratégie d'autorisation à la liste.  
  
4.  Répétez les étapes 2 et 3 pour chaque stratégie d'autorisation personnalisée à ajouter.  
  
5.  Assignez une version en lecture seule de la liste à la propriété <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>.  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## Exemple  
 Dans l'exemple suivant, la stratégie <xref:System.IdentityModel.Policy.IAuthorizationPolicy> est implémentée de manière exhaustive.  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## Voir aussi  
 <xref:System.ServiceModel.ServiceAuthorizationManager>   
 [Comment : comparer des revendications](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)   
 [Comment : créer un gestionnaire d'autorisations personnalisé pour un service](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)   
 [Authorization Policy](../../../../docs/framework/wcf/samples/authorization-policy.md)