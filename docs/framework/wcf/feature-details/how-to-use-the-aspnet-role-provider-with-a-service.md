---
title: "Comment : utiliser le fournisseur de rôle ASP.NET avec un service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bdddbd39a528e6abd6a0268db310b6173849f19b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="e3d71-102">Comment : utiliser le fournisseur de rôle ASP.NET avec un service</span><span class="sxs-lookup"><span data-stu-id="e3d71-102">How to: Use the ASP.NET Role Provider with a Service</span></span>
<span data-ttu-id="e3d71-103">Le fournisseur de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] (conjointement au fournisseur d'appartenances [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ) est une fonctionnalité qui permet aux développeurs [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de créer des sites Web permettant aux utilisateurs de créer un compte avec un site et d'être affectés d'un rôle à des fins d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="e3d71-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider (in conjunction with the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider) is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="e3d71-104">Grâce à cette fonctionnalité, les utilisateurs peuvent établir un compte avec le site et disposer d'un accès exclusif à celui-ci et à ses services.</span><span class="sxs-lookup"><span data-stu-id="e3d71-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="e3d71-105">Cette approche diffère de la sécurité Windows, qui requiert que les utilisateurs disposent de comptes dans un domaine Windows.</span><span class="sxs-lookup"><span data-stu-id="e3d71-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="e3d71-106">Au lieu de cela, tout utilisateur qui fournit ses informations d'identification (combinaison nom d'utilisateur/mot de passe) peut utiliser le site et ses services.</span><span class="sxs-lookup"><span data-stu-id="e3d71-106">Instead, any user who supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="e3d71-107">Pour un exemple d’application, consultez [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="e3d71-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="e3d71-108">le [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fonctionnalité de fournisseur d’appartenance, consultez [Comment : utiliser le fournisseur d’appartenances ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="e3d71-108"> the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
 <span data-ttu-id="e3d71-109">La fonctionnalité de fournisseur de rôle utilise une base de données SQL Server pour stocker des informations utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e3d71-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="e3d71-110">Les développeurs [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] peuvent tirer parti de ces fonctionnalités à des fins de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e3d71-110">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="e3d71-111">En cas d'intégration dans une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les utilisateurs doivent fournir une combinaison nom d'utilisateur/mot de passe à l'application cliente [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3d71-111">When integrated into a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, users must supply a user name/password combination to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span> <span data-ttu-id="e3d71-112">Pour permettre à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] d'utiliser la base de données, vous devez créer une instance de la classe <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>, affectez à sa propriété <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> la valeur <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> et ajoutez l'instance à la collection de comportements au <xref:System.ServiceModel.ServiceHost> qui héberge le service.</span><span class="sxs-lookup"><span data-stu-id="e3d71-112">To enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
### <a name="to-configure-the-role-provider"></a><span data-ttu-id="e3d71-113">Pour configurer le fournisseur de rôle</span><span class="sxs-lookup"><span data-stu-id="e3d71-113">To configure the role provider</span></span>  
  
1.  <span data-ttu-id="e3d71-114">Dans le fichier Web.config, sous le <`system.web`> élément, ajouter un <`roleManager`> et définissez son `enabled` attribut `true`.</span><span class="sxs-lookup"><span data-stu-id="e3d71-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2.  <span data-ttu-id="e3d71-115">Affectez à l'attribut `defaultProvider` la valeur `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="e3d71-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3.  <span data-ttu-id="e3d71-116">En tant qu’enfant à la <`roleManager`> élément, ajouter un <`providers`> élément.</span><span class="sxs-lookup"><span data-stu-id="e3d71-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4.  <span data-ttu-id="e3d71-117">En tant qu’enfant à la <`providers`> élément, ajouter une <`add`> élément avec les attributs suivants ont des valeurs appropriées : `name`, `type`, `connectionStringName`, et `applicationName`, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e3d71-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"   
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="e3d71-118">Pour configurer le service pour utiliser le fournisseur de rôle</span><span class="sxs-lookup"><span data-stu-id="e3d71-118">To configure the service to use the role provider</span></span>  
  
1.  <span data-ttu-id="e3d71-119">Dans le fichier Web.config, ajoutez un [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) élément.</span><span class="sxs-lookup"><span data-stu-id="e3d71-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="e3d71-120">Ajouter un [ \<comportements >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) élément à la <`system.ServiceModel`> élément.</span><span class="sxs-lookup"><span data-stu-id="e3d71-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3.  <span data-ttu-id="e3d71-121">Ajouter un [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) à la <`behaviors`> élément.</span><span class="sxs-lookup"><span data-stu-id="e3d71-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4.  <span data-ttu-id="e3d71-122">Ajouter un [ \<comportement >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) et affectez le `name` attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="e3d71-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5.  <span data-ttu-id="e3d71-123">Ajouter un [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) à la <`behavior`> élément.</span><span class="sxs-lookup"><span data-stu-id="e3d71-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6.  <span data-ttu-id="e3d71-124">Affectez à l'attribut `principalPermissionMode` la valeur `UseAspNetRoles`.</span><span class="sxs-lookup"><span data-stu-id="e3d71-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7.  <span data-ttu-id="e3d71-125">Affectez à l'attribut `roleProviderName` la valeur `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="e3d71-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="e3d71-126">L'exemple suivant présente un fragment de la configuration.</span><span class="sxs-lookup"><span data-stu-id="e3d71-126">The following example shows a fragment of the configuration.</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e3d71-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3d71-127">See Also</span></span>  
 [<span data-ttu-id="e3d71-128">Fournisseur d’appartenances et rôle</span><span class="sxs-lookup"><span data-stu-id="e3d71-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 [<span data-ttu-id="e3d71-129">Comment : utiliser le fournisseur d’appartenances ASP.NET</span><span class="sxs-lookup"><span data-stu-id="e3d71-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
