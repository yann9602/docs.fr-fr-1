---
title: "&lt;réseau&gt; élément (paramètres réseau)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 679351fd2d6f0727d40bd57c9ef2016738462eb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetworkgt-element-network-settings"></a><span data-ttu-id="1df29-102">&lt;réseau&gt; élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="1df29-102">&lt;network&gt; Element (Network Settings)</span></span>
<span data-ttu-id="1df29-103">Configure les options réseau pour un serveur SMTP Simple Mail Transport Protocol () externe.</span><span class="sxs-lookup"><span data-stu-id="1df29-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="1df29-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="1df29-104">\<configuration></span></span>  
<span data-ttu-id="1df29-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="1df29-105">\<system.net></span></span>  
<span data-ttu-id="1df29-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="1df29-106">\<mailSettings></span></span>  
<span data-ttu-id="1df29-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="1df29-107">\<smtp></span></span>  
<span data-ttu-id="1df29-108">\<réseau ></span><span class="sxs-lookup"><span data-stu-id="1df29-108">\<network></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1df29-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1df29-109">Syntax</span></span>  
  
```xml  
<network  
  clientDomain="string"   
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"   
  password="string"  
  port="integer"   
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1df29-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1df29-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1df29-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1df29-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1df29-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="1df29-112">Attributes</span></span>  
  
|<span data-ttu-id="1df29-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="1df29-113">Attribute</span></span>|<span data-ttu-id="1df29-114">Description</span><span class="sxs-lookup"><span data-stu-id="1df29-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="1df29-115">Spécifie le nom de domaine client à utiliser dans la requête initiale de protocole SMTP pour se connecter au serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="1df29-116">La valeur par défaut est le nom d’hôte local de l’ordinateur local envoie la demande.</span><span class="sxs-lookup"><span data-stu-id="1df29-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="1df29-117">Spécifie si les informations d’identification des utilisateurs par défaut doivent être utilisées pour accéder au serveur de messagerie SMTP pour les transactions SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="1df29-118">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="1df29-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="1df29-119">Indique si SSL est utilisé pour accéder à un serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="1df29-120">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="1df29-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="1df29-121">Spécifie le nom d’hôte du serveur de messagerie SMTP à utiliser pour les transactions SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="1df29-122">Il n’y a aucune valeur par défaut pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="1df29-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="1df29-123">Spécifie le mot de passe à utiliser pour l’authentification sur le serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="1df29-124">Il n’y a aucune valeur par défaut pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="1df29-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="1df29-125">Spécifie le numéro de port à utiliser pour se connecter au serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="1df29-126">La valeur par défaut est 25.</span><span class="sxs-lookup"><span data-stu-id="1df29-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="1df29-127">Spécifie le nom de fournisseur de Service (SPN) à utiliser pour l’authentification lors de l’utilisation de la protection étendue pour les transactions SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="1df29-128">Il n’y a aucune valeur par défaut pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="1df29-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="1df29-129">Spécifie le nom d’utilisateur à utiliser pour l’authentification sur le serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="1df29-130">Il n’y a aucune valeur par défaut pour cet attribut.</span><span class="sxs-lookup"><span data-stu-id="1df29-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1df29-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1df29-131">Child Elements</span></span>  
 <span data-ttu-id="1df29-132">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1df29-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1df29-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1df29-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1df29-134">Élément</span><span class="sxs-lookup"><span data-stu-id="1df29-134">Element</span></span>|<span data-ttu-id="1df29-135">Description</span><span class="sxs-lookup"><span data-stu-id="1df29-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1df29-136">\<SMTP >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="1df29-136">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="1df29-137">Configure les options d’envoi du courrier SMTP Simple Mail Transport Protocol ().</span><span class="sxs-lookup"><span data-stu-id="1df29-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1df29-138">Remarques</span><span class="sxs-lookup"><span data-stu-id="1df29-138">Remarks</span></span>  
 <span data-ttu-id="1df29-139">Certains serveurs SMTP exigent que vous vous authentifier auprès du serveur avant des utiliser.</span><span class="sxs-lookup"><span data-stu-id="1df29-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="1df29-140">Si vous souhaitez vous authentifier en utilisant les informations d’identification de réseau par défaut sur votre ordinateur hôte, définissez le `defaultCredentials` attribut `true`.</span><span class="sxs-lookup"><span data-stu-id="1df29-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="1df29-141">Le <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> propriété peut être utilisée pour obtenir la valeur actuelle de la `defaultCredentials` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="1df29-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="1df29-142">Vous pouvez également utiliser l’authentification de base (nom d’utilisateur et mot de passe) pour vous authentifier auprès du serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="1df29-143">Pour utiliser cette option, vous devez spécifier un nom d’utilisateur valide et un mot de passe pour le serveur SMTP spécifié.</span><span class="sxs-lookup"><span data-stu-id="1df29-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1df29-144">L’authentification de base envoie les `userName` et `password` valeurs non chiffrées au serveur.</span><span class="sxs-lookup"><span data-stu-id="1df29-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="1df29-145">Toute personne analyse du trafic réseau peut afficher vos informations d’identification et les utiliser pour se connecter au serveur.</span><span class="sxs-lookup"><span data-stu-id="1df29-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="1df29-146">Vous devez envisager d’utiliser un mécanisme d’authentification plus sécurisé, telles que Kerberos ou NT LAN Manager (NTLM). Si `defaultCredentials` est `true`, Kerberos ou NTLM sera utilisé si le serveur prend en charge ces protocoles.</span><span class="sxs-lookup"><span data-stu-id="1df29-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="1df29-147">Les options informations d’identification réseau par défaut et l’authentification de base s’excluent mutuellement ; Si vous définissez `defaultCredentials` à `true` et spécifiez un nom d’utilisateur et un mot de passe, les informations d’identification de réseau par défaut sont utilisée, et les données de l’authentification de base sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="1df29-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="1df29-148">L’authentification de base si vous spécifiez un `userName`, vous devez également spécifier un `password` à l’authentification de vous-même au serveur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="1df29-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="1df29-149">Le <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> propriété peut être utilisée pour obtenir la valeur actuelle de la `userName` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="1df29-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="1df29-150">Le <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> propriété peut être utilisée pour obtenir la valeur actuelle de la `password` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="1df29-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="1df29-151">A `password` attribut ne serait pas entré normalement dans les fichiers de configuration pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1df29-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="1df29-152">Le `clientDomain` attribut modifie le nom de domaine client utilisé dans la requête initiale de protocole SMTP à un serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="1df29-153">Le `clientDomain` attribut peut être défini sur le nom de domaine complet de l’ordinateur local, plutôt que le nom d’hôte local qui est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="1df29-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="1df29-154">Cela fournit une plus grande compatibilité avec les normes de protocole SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="1df29-155">La valeur par défaut est le nom d’hôte local de l’ordinateur local envoie la demande.</span><span class="sxs-lookup"><span data-stu-id="1df29-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="1df29-156">Le <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> propriété peut être utilisée pour obtenir la valeur actuelle de la `clientDomain` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="1df29-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="1df29-157">Le `targetName` attribut est utilisé pour l’authentification lors de l’utilisation de la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="1df29-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="1df29-158">La valeur par défaut est de la forme « SMTPSVC /\<hôte > » où \<hôte > est le nom d’hôte du serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="1df29-159">Le <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> propriété peut être utilisée pour obtenir la valeur actuelle de la `targetName` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="1df29-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="1df29-160">Le `enableSsl` attribut spécifie si SSL est utilisé pour accéder à un serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="1df29-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="1df29-161">La <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> classe uniquement prend en charge l’Extension du Service SMTP pour SMTP sécurisé sur le protocole TLS tel que défini dans RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="1df29-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="1df29-162">Dans ce mode, la session SMTP commence sur un canal non chiffré, puis une commande STARTTLS est émise par le client au serveur pour basculer vers une communication sécurisée à l’aide de SSL.</span><span class="sxs-lookup"><span data-stu-id="1df29-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="1df29-163">Consultez la RFC 3207 publiée par l’IETF Internet Engineering Task Force () pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="1df29-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="1df29-164">Une autre méthode de connexion est où une session SSL est établie au préalable avant un autre protocole que les commandes sont envoyées.</span><span class="sxs-lookup"><span data-stu-id="1df29-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="1df29-165">Cette méthode de connexion est parfois appelée SMTPS et utilise par défaut le port 465.</span><span class="sxs-lookup"><span data-stu-id="1df29-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="1df29-166">Cette autre méthode de connexion à l’aide de SSL n’est pas pris en charge actuellement.</span><span class="sxs-lookup"><span data-stu-id="1df29-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="1df29-167">Le <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> propriété peut être utilisée pour obtenir la valeur actuelle de la `enableSsl` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="1df29-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1df29-168">Exemple</span><span class="sxs-lookup"><span data-stu-id="1df29-168">Example</span></span>  
 <span data-ttu-id="1df29-169">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques en utilisant les informations d’identification de réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="1df29-169">The following example specifies the appropriate SMTP parameters to send e-mail using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1df29-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1df29-170">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 [<span data-ttu-id="1df29-171">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="1df29-171">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
