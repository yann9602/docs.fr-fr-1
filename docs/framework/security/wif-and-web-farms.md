---
title: "WIF et batteries de serveurs web | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc3cd7fa-2b45-4614-a44f-8fa9b9d15284
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# WIF et batteries de serveurs web
Lorsque vous utilisez Windows Identity Foundation \(WIF\) pour sécuriser les ressources d'une application \(RP\) partie utilisatrice qui est déployé dans une batterie de serveurs web, vous devez prendre des mesures spécifiques afin de garantir que les WIF peut traiter des jetons à partir des instances de l'application de RP en cours d'exécution sur des ordinateurs différents de la batterie.  Ce traitement comprend la validation des signatures de jeton de session, le cryptage et décryptage des jetons de session, la mise en cache des jetons de session et détection de relecture de jetons de sécurité.  
  
 Dans la plupart des cas, lorsque WIF est utilisé pour sécuriser les ressources d'une application RP – si le RP est en cours d'exécution sur un ordinateur unique ou dans une batterie de serveurs web\-\-une session est établie avec le client basé sur le jeton de sécurité qui ont été obtenu auprès du service de jeton de sécurité \(STS\).  Il s'agit de ne pas forcer le client à s'authentifier à la STS pour chaque ressource d'application est sécurisée à l'aide de WIF.  Pour plus d'informations sur la façon dont WIF gère les sessions, consultez [Gestion de session WIF](../../../docs/framework/security/wif-session-management.md).  
  
 Lorsque les paramètres par défaut sont utilisés, WIF effectue les opérations suivantes :  
  
-   Il utilise une instance de la <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe pour lire et écrire un jeton de session \(une instance de la <xref:System.IdentityModel.Tokens.SessionSecurityToken> classe\) qui transporte les revendications et autres informations sur le jeton de sécurité qui a été utilisé pour l'authentification ainsi que des informations sur la session elle\-même.  Le jeton de session est emballé et entreposée dans un cookie de session.  Par défaut, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> utilise le <xref:System.IdentityModel.ProtectedDataCookieTransform> \(classe\), qui utilise l'API de Protection des données \(DPAPI\) pour protéger le jeton de session.  Le DPAPI offre une protection en utilisant les informations d'identification utilisateur ou ordinateur et stocke les données de clés dans le profil utilisateur.  
  
-   Il utilise un par défaut, la mise en oeuvre en mémoire de le <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe pour stocker et traiter le jeton de session.  
  
 Ces paramètres par défaut fonctionnent dans les scénarios dans lesquels l'application RP est déployée sur un seul ordinateur ; Toutefois, lorsqu'il est déployé dans une batterie de serveurs web, chaque requête HTTP peut envoyé à et traité par une autre instance de l'application de RP en cours d'exécution sur un autre ordinateur.  Dans ce scénario, les paramètres de WIF par défaut décrits ci\-dessus ne fonctionnera pas car le jeton protection et la mise en cache des jetons sont dépendantes sur un ordinateur spécifique.  
  
 Pour déployer une application RP dans une batterie de serveurs web, vous devez vous assurer que le traitement des jetons de session \(ainsi que des jetons relus\) n'est pas dépendant de l'application s'exécutant sur un ordinateur spécifique.  Pour ce faire consiste à implémenter votre application RP afin qu'il utilise la fonctionnalité fournie par le runtime ASP..NET `<machineKey>` élément de configuration et fournit une mise en cache distribuée pour le traitement des jetons de session et relus jetons.  Le `<machineKey>` élément vous permet de spécifier les clés nécessaires pour valider, crypter et décrypter les jetons dans un fichier de configuration qui permet de spécifier les mêmes clés sur des ordinateurs différents dans la batterie de serveurs web.  WIF fournit un gestionnaire de jetons de session spécialisé, le <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>, qui protège les jetons en utilisant les touches spécifiées dans la `<machineKey>` élément.  Pour mettre en œuvre cette stratégie, vous pouvez suivre ces instructions :  
  
-   Utiliser l'application ASP.NET `<machineKey>` élément de configuration pour spécifier explicitement les clés de signature et de cryptage peuvent être utilisés sur plusieurs ordinateurs de la batterie.  Le code XML suivant illustre la spécification de la `<machineKey>` élément sous la `<system.web>` élément dans un fichier de configuration.  
  
    ```xml  
    <machineKey compatibilityMode="Framework45" decryptionKey="CC510D … 8925E6" validationKey="BEAC8 … 6A4B1DE" />  
    ```  
  
-   Configurer l'application pour utiliser le <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> en l'ajoutant à la collection de gestionnaires de jeton.  Vous devez d'abord supprimer la <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> \(ou dérivé de n'importe quel gestionnaire la <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> classe\) à partir de la collection de gestionnaires de jeton si un tel gestionnaire est présent.  Le <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> utilise le <xref:System.IdentityModel.Services.MachineKeyTransform> \(classe\), qui protège les données de cookie de session en utilisant le matériau de chiffrement spécifié dans le `<machineKey>` élément.  Le code XML suivant montre comment ajouter le <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler> à une collection de gestionnaires de jeton.  
  
    ```xml  
    <securityTokenHandlers>  
      <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
      <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    </securityTokenHandlers>  
    ```  
  
-   Dériver de <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> et mettre en œuvre distribués la mise en cache, en d'autres termes, un cache qui est accessible à partir de tous les ordinateurs de la batterie de serveurs sur lesquels le RP peut s'exécuter.  Configurer le RP puisse utiliser votre cache distribué en spécifiant la [\<sessionSecurityTokenCache\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) élément dans le fichier de configuration.  Vous pouvez substituer la <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A?displayProperty=fullName> méthode dans votre classe dérivée pour implémenter les éléments enfants de le `<sessionSecurityTokenCache>` élément s'ils sont requis.  
  
    ```xml  
    <caches>  
      <sessionSecurityTokenCache type="MyCacheLibrary.MySharedSessionSecurityTokenCache, MyCacheLibrary">  
        <!—optional child configuration elements, if implemented by the derived class -->  
      </sessionSecurityTokenCache>  
    </caches>  
    ```  
  
     Une façon de mettre en œuvre la mise en cache distribuée est de fournir un front\-end WCF pour votre cache personnalisé.  Pour plus d'informations sur l'implémentation d'un service de mise en cache de WCF, consultez [Le Service de mise en cache de WCF](#BKMK_TheWCFCachingService).  Pour plus d'informations sur l'implémentation d'un client WCF que l'application RP peut utiliser pour appeler le service de mise en cache, voir [Le Client de mise en cache de WCF](#BKMK_TheWCFClient).  
  
-   Si votre application détecte les jetons relus vous devez suivre une procédure similaire distribué à la mise en cache de stratégie pour le cache de relecture du jeton en dérivant de <xref:System.IdentityModel.Tokens.TokenReplayCache> et pointant vers votre jeton de relire le service de mise en cache dans le [\<tokenReplayCache\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) élément de configuration.  
  
> [!IMPORTANT]
>  Tous l'exemple de code XML et le code dans cette rubrique provient de la [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) \(http:\/\/go.Microsoft.com\/fwlink\/?LinkID\=248408\) échantillon.  
  
> [!IMPORTANT]
>  Les exemples de cette rubrique sont fournis en tant que\-est et ne sont pas destinés à être utilisés dans le code de production sans modification.  
  
<a name="BKMK_TheWCFCachingService"></a>   
## Le Service de mise en cache de WCF  
 L'interface suivante définit le contrat entre le service de mise en cache de WCF et le client WCF utilisé par l'application de partie utilisatrice de communiquer avec lui.  Elle expose essentiellement les méthodes de la <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe en tant qu'opérations de service.  
  
```  
[ServiceContract()]  
public interface ISessionSecurityTokenCacheService  
{  
    [OperationContract]  
    void AddOrUpdate(string endpointId, string contextId, string keyGeneration, SessionSecurityToken value, DateTime expiryTime);  
  
    [OperationContract]  
    IEnumerable<SessionSecurityToken> GetAll(string endpointId, string contextId);  
  
    [OperationContract]  
    SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration);  
  
    [OperationContract(Name = "RemoveAll")]  
    void RemoveAll(string endpointId, string contextId);  
  
    [OperationContract(Name = "RemoveAllByEndpointId")]  
    void RemoveAll(string endpointId);  
  
    [OperationContract]  
    void Remove(string endpointId, string contextId, string keyGeneration);  
}  
```  
  
 Le code suivant illustre l'implémentation de WCF service de mise en cache.  Dans cet exemple, la valeur par défaut, le cache de jetons de session en mémoire implémentée par WIF est utilisé.  Également, vous pourriez implémenter un cache durable soutenu par une base de données.  `ISessionSecurityTokenCacheService`Définit l'interface présentée ci\-dessus.  Dans cet exemple, toutes les méthodes requises pour implémenter l'interface sont affichés par souci de concision.  
  
```  
using System;  
using System.Collections.Generic;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace WcfSessionSecurityTokenCacheService  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class SessionSecurityTokenCacheService : ISessionSecurityTokenCacheService  
    {  
        SessionSecurityTokenCache internalCache;  
  
        // sets the internal cache used by the service to the default WIF in-memory cache.  
        public SessionSecurityTokenCacheService()  
        {  
            internalCache = new IdentityModelCaches().SessionSecurityTokenCache;  
        }  
  
        ...  
  
        public SessionSecurityToken Get(string endpointId, string contextId, string keyGeneration)  
        {  
            // Delegates to the default, in-memory MruSessionSecurityTokenCache used by WIF  
            SessionSecurityToken token = internalCache.Get(new SessionSecurityTokenCacheKey(endpointId, GetContextId(contextId), GetKeyGeneration(keyGeneration)));  
            return token;  
        }  
  
        ...  
  
        private static UniqueId GetContextId(string contextIdString)  
        {  
            return contextIdString == null ? null : new UniqueId(contextIdString);  
        }  
  
        private static UniqueId GetKeyGeneration(string keyGenerationString)  
        {  
            return keyGenerationString == null ? null : new UniqueId(keyGenerationString);  
        }  
    }  
}  
```  
  
<a name="BKMK_TheWCFClient"></a>   
## Le Client de mise en cache de WCF  
 Cette section présente l'implémentation d'une classe qui dérive de <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> et que les délégués appelle le service de mise en cache.  Vous configurez l'application RP pour utiliser cette classe par le biais de la [\<sessionSecurityTokenCache\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md) élément comme dans le code XML suivant  
  
```  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
 La substitution de la classe le <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache.LoadCustomConfiguration%2A> méthode pour obtenir le point de terminaison de service à partir de la custom `<cacheServiceAddress>` élément enfant de le `<sessionSecurityTokenCache>` élément.  Il utilise ce point de terminaison pour initialiser un `ISessionSecurityTokenCacheService` canal sur lequel il peut communiquer avec le service.  Dans cet exemple, toutes les méthodes requises pour implémenter la <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe sont affichés par souci de concision.  
  
```  
using System;  
using System.Configuration;  
using System.IdentityModel.Configuration;  
using System.IdentityModel.Tokens;  
using System.ServiceModel;  
using System.Xml;  
  
namespace CacheLibrary  
{  
    /// <summary>  
    /// This class acts as a proxy to the WcfSessionSecurityTokenCacheService.  
    /// </summary>  
    public class SharedSessionSecurityTokenCache : SessionSecurityTokenCache, ICustomIdentityConfiguration  
    {  
        private ISessionSecurityTokenCacheService WcfSessionSecurityTokenCacheServiceClient;  
  
        internal SharedSessionSecurityTokenCache()  
        {  
        }  
  
        /// <summary>  
        /// Creates a client channel to call the service host.  
        /// </summary>  
        protected void Initialize(string cacheServiceAddress)  
        {  
            if (this.WcfSessionSecurityTokenCacheServiceClient != null)  
            {  
                return;  
            }  
  
            ChannelFactory<ISessionSecurityTokenCacheService> cf = new ChannelFactory<ISessionSecurityTokenCacheService>(  
                new WS2007HttpBinding(SecurityMode.None),  
                new EndpointAddress(cacheServiceAddress));  
            this.WcfSessionSecurityTokenCacheServiceClient = cf.CreateChannel();  
        }  
  
        #region SessionSecurityTokenCache Members  
        // Delegates the following operations to the centralized session security token cache service in the web farm.  
  
        ...  
  
        public override SessionSecurityToken Get(SessionSecurityTokenCacheKey key)  
        {  
            return this.WcfSessionSecurityTokenCacheServiceClient.Get(key.EndpointId, GetContextIdString(key), GetKeyGenerationString(key));  
        }  
  
        ...  
  
        #endregion  
  
        #region ICustomIdentityConfiguration Members  
        // Called from configuration infrastructure to load custom elements  
        public void LoadCustomConfiguration(XmlNodeList nodeList)  
        {  
            // Retrieve the endpoint address of the centralized session security token cache service running in the web farm  
            if (nodeList.Count == 0)  
            {  
                throw new ConfigurationException("No child config element found under <sessionSecurityTokenCache>.");  
            }  
  
            XmlElement cacheServiceAddressElement = nodeList.Item(0) as XmlElement;  
            if (cacheServiceAddressElement.LocalName != "cacheServiceAddress")  
            {  
                throw new ConfigurationException("First child config element under <sessionSecurityTokenCache> is expected to be <cacheServiceAddress>.");  
            }  
  
            string cacheServiceAddress = null;  
            if (cacheServiceAddressElement.Attributes["url"] != null)  
            {  
                cacheServiceAddress = cacheServiceAddressElement.Attributes["url"].Value;  
            }  
            else  
            {  
                throw new ConfigurationException("<cacheServiceAddress> is expected to contain a 'url' attribute.");  
            }  
  
            // Initialize the proxy to the WebFarmSessionSecurityTokenCacheService  
            this.Initialize(cacheServiceAddress);  
        }  
        #endregion  
  
        private static string GetKeyGenerationString(SessionSecurityTokenCacheKey key)  
        {  
            return key.KeyGeneration == null ? null : key.KeyGeneration.ToString();  
        }  
  
        private static string GetContextIdString(SessionSecurityTokenCacheKey key)  
        {  
            return GetContextIdString(key.ContextId);  
        }  
  
        private static string GetContextIdString(UniqueId contextId)  
        {  
            return contextId == null ? null : contextId.ToString();  
        }  
    }  
}  
```  
  
## Voir aussi  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>   
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>   
 <xref:System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler>   
 [Gestion de session WIF](../../../docs/framework/security/wif-session-management.md)