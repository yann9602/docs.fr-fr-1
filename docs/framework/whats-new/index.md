---
title: "Nouveaut&#233;s dans le .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "04/07/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nouveautés (.NET Framework)"
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
caps.latest.revision: 292
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 287
---
# Nouveaut&#233;s dans le .NET Framework
<a name="introduction"></a>Cet article résume les principales nouvelles fonctionnalités et améliorations dans les versions suivantes du .NET Framework :  
  
 [4.6.2 de .NET framework](#v462)   
 [.NET framework 4.6.1](#v461)   
 [.NET 2015 et .NET Framework 4.6](#v46)   
 [.NET framework 4.5.2](#v452)   
 [.NET framework 4.5.1](#v451)   
 [.NET framework 4.5](#core)  
  
 Cet article ne fournit pas d'informations complètes sur chacune des nouvelles fonctionnalités et peut faire l'objet de modifications. Pour obtenir des informations générales sur le .NET Framework, consultez [mise en route](../../../docs/framework/get-started/index.md). Pour les plateformes prises en charge, consultez la page [requise](../../../docs/framework/get-started/system-requirements.md). Pour des liens de téléchargement et les instructions d’installation, consultez [Guide d’Installation](../../../docs/framework/install/guide-for-developers.md).  
  
> [!NOTE]
>  L’équipe .NET Framework propose également des fonctionnalités hors bande avec NuGet pour étendre la prise en charge de la plate-forme et d’introduire de nouvelles fonctionnalités, telles que les collections immuables et les types de vecteurs compatibles SIMD. Pour plus d’informations, consultez [autres bibliothèques de classes et API](../../../ml/index.xml) et [du .NET Framework et les versions hors-bande](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md). Consultez un [la liste complète des packages NuGet](http://blogs.msdn.com/b/dotnet/p/nugetpackages.aspx) pour le .NET Framework, ou s’y abonner [notre flux](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).  
  
<a name="v462"></a>   
## <a name="introducing-the-net-framework-462"></a>Présentation du .NET Framework 4.6.2  
 Le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] repose sur le .NET Framework versions 4.6 et 4.6.1, auxquelles il ajoute un grand nombre de nouveaux correctifs et plusieurs nouvelles fonctionnalités, tout en restant un produit très stable.  
  
### <a name="downloading-and-installing-the-net-framework-462"></a>Téléchargement et installation du .NET Framework 4.6.2  
 Vous pouvez télécharger le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] à partir des emplacements suivants :  
  
-   [Le programme d’installation de .NET framework 4.6.2 Web](http://go.microsoft.com/fwlink/?LinkId=780597)  
  
-   [Programme d’installation en mode hors connexion de NET Framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780601)  
  
 Le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] peut être installé sur Windows 10, Windows 8.1, Windows 7 et les plateformes de serveur correspondantes à compter de Windows Server 2008 R2 SP1. Vous pouvez installer le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] à l’aide du programme d’installation web ou du programme d’installation hors connexion. Le programme d’installation web constitue la méthode recommandée pour la plupart des utilisateurs.  
  
 Vous pouvez cibler les [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] dans Visual Studio 2012 ou version ultérieure en installant le [Pack du développeur .NET Framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=780617).  
  
### <a name="whats-new-in-the-net-framework-462"></a>Nouveautés du .NET Framework 4.6.2  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] inclut de nouvelles fonctionnalités dans les domaines suivants :  
  
-   [ASP.NET](#ASPNET462)  
  
-   [Catégories de caractères](#Strings)  
  
-   [Cryptographie](#Crypto462)  
  
-   [SqlClient](#SQLClient)  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF462)  
  
-   [Windows Workflow Foundation (WF)](#WF462)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [Conversion des Windows Forms et les applications WPF pour les applications UWP](#UWPConvert)  
  
-   [Améliorations du débogage](#Debug462)  
  
 Pour une liste des nouvelles API ajoutés à la [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], consultez [modifications de l’API .NET Framework 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) sur GitHub. Pour obtenir la liste des améliorations des fonctionnalités et des correctifs de bogues dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], consultez [modifications de l’API .NET Framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=708778) sur GitHub.  Pour plus d’informations, consultez [annonce de .NET Framework 4.6.2](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/) dans le Blog .NET.  
  
<a name="ASPNET462"></a>   
### <a name="aspnet"></a>ASP.NET  
 Dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ASP.NET propose les améliorations suivantes :  
  
 **Prise en charge améliorée pour les messages d’erreur localisés dans les validateurs d’annotation de données**  
 Les validateurs d’annotations de données vous permettent d’effectuer une validation en ajoutant un ou plusieurs attributs à une propriété de classe. L’attribut <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName> élément définit le texte du message d’erreur si la validation échoue. À compter du [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ASP.NET facilite la localisation des messages d’erreur. Les messages d’erreur sont localisés si les conditions suivantes sont réunies :  
  
1.  Le <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName> est fourni dans l’attribut de validation.  
  
2.  Le fichier de ressources est stocké dans le dossier App_LocalResources.  
  
3.  Le nom du fichier des ressources localisées présente sous la forme `DataAnnotation.Localization.{` *nom*`}.resx`, où *nom* est un nom de culture au format *languageCode*`-`*code de pays/région* ou *languageCode*.  
  
4.  Le nom de la clé de la ressource est la chaîne assignée à la <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName> attribut et sa valeur est le message d’erreur localisé.  
  
 Par exemple, l’attribut d’annotation de données suivant définit message d’erreur de la culture par défaut pour un classement non valide.  
  
```csharp  
  
public class RatingInfo  
{  
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]  
   [Display(Name = "Your Rating")]  
   public int Rating { get; set; }  
}  
  
```  
  
```vb  
  
Public Class RatingInfo  
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>  
   <Display(Name = "Your Rating")>  
   Public Property Rating As Integer = 1  
End Class  
  
```  
  
 Vous pouvez ensuite créer un fichier de ressources DataAnnotation.Localization.fr.resx, dont la clé est la chaîne de message d’erreur et dont la valeur est le message d’erreur localisé. Le fichier doit se trouver dans le `App.LocalResources` dossier. Par exemple, voici la clé et sa valeur dans un message d’erreur de langue Français (fr) localisé :  
  
|Nom|Valeur|  
|----------|-----------|  
|L’évaluation doit être compris entre 1 et 10.|Remarque La doit être comprenant entre 1 et 10.|  
  
 Ce fichier peut ensuite  
  
 De plus, la localisation des annotations de données est extensible. Les développeurs peuvent incorporer dans leur propre fournisseur de localisateur de chaîne en implémentant le <xref:System.Web.Globalization.IStringLocalizerProvider> interface pour stocker la chaîne de localisation quelque part autre que dans un fichier de ressources.  
  
 **Prise en charge asynchrone avec les fournisseurs de magasin d’état de session**  
 ASP.NET autorise désormais l’utilisation de méthodes retournant des tâches avec les fournisseurs de magasins d’état de session, ce qui permet ainsi aux applications ASP.NET de profiter de la scalabilité des opérations asynchrones. Enregistrent les fournisseurs à prend en charge les opérations asynchrones avec l’état de session, ASP.NET inclut une nouvelle interface <xref:System.Web.SessionState.ISessionStateModule?displayProperty=fullName>, qui hérite de <xref:System.Web.IHttpModule> permet aux développeurs d’implémenter leurs propres fournisseurs de magasins de session module et async état de session. L’interface se définit comme suit :  
  
```csharp  
  
public interface ISessionStateModule : IHttpModule {  
    void ReleaseSessionState(HttpContext context);  
    Task ReleaseSessionStateAsync(HttpContext context);  
}  
  
```  
  
 En outre, les <xref:System.Web.SessionState.SessionStateUtility> classe inclut deux nouvelles méthodes, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> et <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, qui peut être utilisé pour prendre en charge les opérations asynchrones.  
  
 **Prise en charge asynchrone pour les fournisseurs de cache de sortie**  
 À compter du [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], il est possible d’utiliser des méthodes qui retournent des tâches avec les fournisseurs de cache de sortie de façon à profiter de la scalabilité des opérations asynchrones.  Les fournisseurs qui implémentent ces méthodes réduisent le blocage de threads sur un serveur web et améliorent la scalabilité d’un service ASP.NET.  
  
 Les API suivantes ont été ajoutées pour assurer la prise en charge des fournisseurs de cache de sortie asynchrones :  
  
-   Le <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=fullName> classe qui hérite de <xref:System.Web.Caching.OutputCacheProvider?displayProperty=fullName> permet aux développeurs d’implémenter un fournisseur de cache de sortie asynchrone.  
  
-   Le <xref:System.Web.Caching.OutputCacheUtility> (classe), qui fournit des méthodes d’assistance pour configurer le cache de sortie.  
  
-   nouvelles méthodes de&18; dans le <xref:System.Web.HttpCachePolicy?displayProperty=fullName>(classe). Ceux-ci incluent <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, et <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.  
  
-   2 nouvelles méthodes dans le <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=fullName> classe : <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> et <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.  
  
-   2 nouvelles méthodes dans le <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=fullName> classe : <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> et <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.  
  
-   2 nouvelles méthodes dans le <xref:System.Web.HttpCacheVaryByParams?displayProperty=fullName> classe : <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> et <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.  
  
-   Dans le <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=fullName> (classe), la <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> (méthode).  
  
-   Dans le <xref:System.Web.Caching.CacheDependency>, le <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> (méthode).  
  
<a name="Strings"></a>   
### <a name="character-categories"></a>Catégories de caractères  
 Les caractères de la [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] sont classés en fonction de la [Unicode Standard, Version 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/). Dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], les caractères étaient classés en fonction des catégories de caractères Unicode 6.3.  
  
 Prise en charge d’Unicode 8.0 est limitée à la classification des caractères par le <xref:System.Globalization.CharUnicodeInfo> classe et aux types et méthodes qui reposent dessus. Ceux-ci incluent le <xref:System.Globalization.StringInfo> classe surchargées <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName> (méthode) et le [classes de caractères](../../../docs/standard/base-types/character-classes-in-regular-expressions.md) reconnu par le moteur des expressions régulières .NET Framework.  La comparaison et le tri des caractères et des chaînes ne sont pas affectés par cette évolution et continuent de s’appuyer sur le système d’exploitation sous-jacent ou bien, dans le cas des systèmes Windows 7, sur les données de caractères fournies par le .NET Framework.  
  
 Pour les modifications dans les catégories de caractères Unicode 6.0 à 7.0 d’Unicode, voir [la norme Unicode, Version 7.0.0](http://www.unicode.org/versions/Unicode7.0.0/) sur le site Web du Unicode Consortium. Pour les modifications de Unicode 7.0 Unicode 8.0, consultez [la norme Unicode, Version 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/) sur le site Web du Unicode Consortium.  
  
<a name="Crypto462"></a>   
### <a name="cryptography"></a>Chiffrement  
 **Prise en charge de X509 certificats contenant DSA FIPS 186-3**  
 Le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ajoute la prise en charge des certificats X509 DSA(Digital Signature Algorithm) dont les clés dépassent la limite de 1 024 bits de la norme FIPS 186-2.  
  
 En plus de prendre en charge les clés plus volumineuses de FIPS 186-3, le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] autorise le calcul de signatures à l’aide des algorithmes de hachage de la famille SHA-2 (SHA256, SHA384 et SHA512). FIPS 186-3 est prise par le nouveau <xref:System.Security.Cryptography.DSACng?displayProperty=fullName> (classe).  
  
 Conformément aux modifications récentes de la <xref:System.Security.Cryptography.RSA> classe dans le .NET Framework 4.6 et <xref:System.Security.Cryptography.ECDsa> classe dans le .NET Framework 4.6.1, le <xref:System.Security.Cryptography.DSA> de classe de base abstraite [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] dispose de méthodes supplémentaires pour autoriser les appelants à utiliser cette fonctionnalité sans cast. Vous pouvez appeler la <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=fullName> méthode d’extension pour signer des données, comme le montre l’exemple suivant.  
  
```csharp  
  
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)  
{  
    using (DSA dsa = cert.GetDSAPrivateKey())  
    {  
        return dsa.SignData(data, HashAlgorithmName.SHA384);  
    }  
}  
  
```  
  
```vb  
  
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()  
    Using DSA As DSA = cert.GetDSAPrivateKey()  
        Return DSA.SignData(data, HashAlgorithmName.SHA384)  
    End Using  
End Function  
  
```  
  
 Vous pouvez appeler la <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=fullName> méthode d’extension pour vérifier les données signées, comme le montre l’exemple suivant.  
  
```csharp  
  
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)  
{  
    using (DSA dsa = cert.GetDSAPublicKey())  
    {  
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);  
    }  
}  
  
```  
  
```  
  
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean  
    Using dsa As DSA = cert.GetDSAPublicKey()  
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)  
    End Using  
End Function  
  
```  
  
 **Augmenter la clarté des entrées aux routines de dérivation de clé ECDiffieHellman**  
 La prise en charge de l’accord d’échange de clés Curve Diffie-Hellman basé sur les courbes elliptiques avait été ajoutée au .NET Framework 3.5 avec trois routines de fonction de dérivation de clés (KDF) différentes. Les entrées pour les routines et les routines eux-mêmes, ont été configurées via les propriétés sur le <xref:System.Security.Cryptography.ECDiffieHellmanCng> objet. Mais comme les routines ne pouvaient pas toutes lire chaque propriété d’entrée, la confusion était de mise auprès des développeurs.  
  
 Pour résoudre ce problème dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], les trois méthodes suivantes ont été ajoutées à la <xref:System.Security.Cryptography.ECDiffieHellman> classe pour représenter plus clairement ces routines KDF et leurs entrées de base :  
  
|Méthode ECDiffieHellman|Description|  
|----------------------------|-----------------|  
|[DeriveKeyFromHash (ECDiffieHellmanPublicKey, HashAlgorithmName, octet\[\], octet\<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Dérive le matériel de clé à l’aide de la formule<br /><br /> Hash(secretPrepend || *x* || secretAppend)<br /><br /> HACHAGE (secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> où *x* est le résultat de l’algorithme Diffie-Hellman de ce calculée.|  
|[DeriveKeyFromHmac (ECDiffieHellmanPublicKey, HashAlgorithmName, octet\[\], octet\[\], octet\<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Dérive le matériel de clé à l’aide de la formule<br /><br /> HMAC (hmacKey, secretPrepend || *x* || secretAppend)<br /><br /> HMAC (hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> où *x* est le résultat de l’algorithme Diffie-Hellman de ce calculée.|  
|[DeriveKeyTls (ECDiffieHellmanPublicKey, Byte\[\], octet\<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Dérive le matériel de clé à l’aide de l’algorithme de dérivation de la fonction pseudo-aléatoire (PRF) TLS.|  
  
 **Prise en charge pour le chiffrement symétrique clé persistante**  
 La bibliothèque de chiffrement Windows (CNG) avait ajouté la prise en charge du stockage de clés symétriques persistantes et de l’utilisation des clés symétriques stockées sur du matériel, et le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] avait permis aux développeurs d’utiliser cette fonctionnalité.  Sachant que la notion de noms de clés et de fournisseurs de clés est spécifique à l’implémentation, cette fonctionnalité impose l’utilisation du constructeur des types d’implémentation concrets plutôt que l’approche par défaut privilégiée (comme l’appel de `Aes.Create`).  
  
 Prise en charge du cryptage symétrique clé persistante existe pour l’algorithme AES (<xref:System.Security.Cryptography.AesCng>) et 3DES (<xref:System.Security.Cryptography.TripleDESCng>) des algorithmes. Exemple :  
  
```csharp  
  
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)  
{  
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))  
    {  
        aes.IV = iv;  
  
        // Using the zero-argument overload is required to make use of the persisted key  
        using (ICryptoTransform encryptor = aes.CreateEncryptor())  
        {  
            if (!encryptor.CanTransformMultipleBlocks)  
            {  
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");  
            }  
  
            return encryptor.TransformFinalBlock(data, 0, data.Length);  
        }  
    }  
}  
  
```  
  
```vb  
  
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()  
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)  
        Aes.IV = iv  
  
        ' Using the zero-argument overload Is required to make use of the persisted key  
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()  
            If Not encryptor.CanTransformMultipleBlocks Then  
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")  
            End If  
            Return encryptor.TransformFinalBlock(data, 0, data.Length)  
        End Using  
    End Using  
End Function  
  
```  
  
 **Prise en charge SignedXml de hachage SHA-2**  
 Le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] prise en charge pour le <xref:System.Security.Cryptography.Xml.SignedXml> classe pour les méthodes de signature RSA-SHA256, RSA-SHA384 et SHA512 de RSA PKCS&#1; et référence SHA256, SHA384 et SHA512 algorithmes digest.  
  
 Les constantes URI sont exposés sur <xref:System.Security.Cryptography.Xml.SignedXml>:  
  
|Champ SignedXml|Constante|  
|---------------------|--------------|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|  
  
 Tous les programmes que vous ont enregistré un personnalisé <xref:System.Security.Cryptography.SignatureDescription> gestionnaire dans <xref:System.Security.Cryptography.CryptoConfig> pour ajouter la prise en charge pour ces algorithmes continueront à fonctionner comme ils le faisaient dans le passé, mais dans la mesure où il existe maintenant plateforme par défaut, le <xref:System.Security.Cryptography.CryptoConfig> inscription n’est plus nécessaire.  
  
<a name="SQLClient"></a>   
### <a name="sqlclient"></a>SqlClient  
 Fournisseur de données .NET framework pour SQL Server (<xref:System.Data.SqlClient?displayProperty=fullName>) inclut les nouvelles fonctionnalités suivantes dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]:  
  
 **Le regroupement de connexions et de délais d’attente avec les bases de données SQL Azure**  
 Quand le regroupement de connexions est activé et qu’une expiration de délai ou toute autre erreur de connexion se produit, une exception est mise en cache ; cette exception mise en cache est levée chaque fois qu’une nouvelle tentative de connexion intervient entre 5 secondes et 1 minute après.  Pour plus d’informations, consultez [le regroupement de connexion serveur SQL (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
 Ce comportement n’est pas souhaitable quand il s’agit d’établir des connexions à des bases de données Azure SQL Database, car les tentatives de connexion peuvent échouer avec des erreurs transitoires qui sont en général récupérées rapidement. Pour des nouvelles tentatives de connexion plus abouties, le comportement de période de blocage de pool de connexions est supprimé quand les connexions aux bases de données Azure SQL Database échouent.  
  
 L’ajout du nouveau mot clé `PoolBlockingPeriod` vous permet de sélectionner la période de blocage qui convient le mieux à votre application. Les valeurs incluent :  
  
 `Auto`  
 La période de blocage de pool de connexions d’une application qui se connecte à une base de données Azure SQL Database est désactivée, pendant que celle d’une application qui se connecte à une autre instance SQL Server est activée. Valeur par défaut. Si le nom de point de terminaison d’un serveur se termine par l’un des éléments suivants, il est considéré comme une base de données Azure SQL Database :  
  
-   .database.windows.net  
  
-   .database.chinacloudapi.cn  
  
-   .database.usgovcloudapi.net  
  
-   .database.cloudapi.de  
  
 `AlwaysBlock`  
 La période de blocage de pool de connexion est toujours activée.  
  
 `NeverBlock`  
 La période de blocage de pool de connexion est toujours désactivée.  
  
 **Améliorations pour toujours chiffrées**  
 SQLClient inaugure deux améliorations pour Always Encrypted :  
  
-   Pour améliorer les performances des requêtes paramétrables sur des colonnes de base de données chiffrées, les métadonnées de chiffrement sont désormais mises en cache pour les paramètres des requêtes. Avec le <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=fullName> propriété `true` (qui est la valeur par défaut), si la même requête est appelée plusieurs fois, le client récupère des métadonnées de paramètre à partir du serveur une seule fois.  
  
-   Entrées de clé de chiffrement colonne dans le cache des clés sont désormais supprimées après un délai configurable à l’aide de la <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=fullName> propriété.  
  
<a name="WCF"></a>   
### <a name="windows-communication-foundation"></a>Windows Communication Foundation  
 Dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Communication Foundation a été amélioré dans les domaines suivants :  
  
 **Prise en charge de sécurité de transport WCF pour les certificats stockés à l’aide de CNG**  
 La sécurité du transport WCF prend en charge les certificats stockés à l’aide de la bibliothèque de chiffrement Windows (CNG). Dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], cette prise en charge se limite à l’utilisation de certificats avec une clé publique dont l’exposant ne dépasse pas 32 bits de longueur. Quand une application cible le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], cette fonctionnalité est activée par défaut.  
  
 Pour les applications qui ciblent le [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] et antérieures mais sont en cours d’exécution le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], cette fonctionnalité peut être activée en ajoutant la ligne suivante à la [ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section du fichier app.config ou web.config.  
  
```xml  
  
<AppContextSwitchOverrides  
    value="Switch.System.ServiceModel.DisableCngCertificates=false"  
/>  
  
```  
  
 Vous pouvez en faire autant par programmation avec un code de ce type :  
  
```csharp  
  
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";  
AppContext.SetSwitch(disableCngCertificates, false);  
  
```  
  
```vb  
  
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"  
AppContext.SetSwitch(disableCngCertificates, False)  
  
```  
  
 **Meilleure prise en charge de plusieurs règles d’ajustement de l’heure d’été par la classe DataContractJsonSerializer**  
 Clients peuvent utiliser un paramètre de configuration d’application pour déterminer si les <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> classe prend en charge plusieurs règles d’ajustement d’un fuseau horaire. Il est nécessaire d'accepter cette fonctionnalité. Pour l’activer, ajoutez le paramètre suivant à votre fichier app.config :  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />  
</runtime>  
  
```  
  
 Lorsque cette fonctionnalité est activée, un <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object utilise le <xref:System.TimeZoneInfo> type au lieu de la <xref:System.TimeZone> type pour désérialiser des données de date et d’heure. <xref:System.TimeZoneInfo> prend en charge plusieurs règles d’ajustement, qui permet de manipuler les données historiques de fuseau horaire ;   <xref:System.TimeZone> pas.  
  
 Pour plus d’informations sur la <xref:System.TimeZoneInfo> structure et ajustement de fuseau horaire, consultez [vue d’ensemble du fuseau horaire](../../../docs/standard/datetime/time-zone-overview.md).  
  
 **Prise en charge de la conservation d’un heure UTC heure sérialisation et désérialisation avec la classe XMLSerializer**  
 En règle générale, lorsque le <xref:System.Xml.Serialization.XmlSerializer> classe est utilisée pour sérialiser un UTC <xref:System.DateTime> valeur, il crée une chaîne d’heure sérialisée qui préserve la date et l’heure, mais suppose que l’heure est local.  Par exemple, si vous instanciez une date et une heure UTC en appelant le code suivant :  
  
```csharp  
DateTime utc = new DateTime(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc);  
```  
  
```vb  
Dim utc As New Date(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc)  
```  
  
 Vous obtenez la chaîne d’heure sérialisée « 03:00:00.0000000-08:00 » pour un système avec huit heures de moins par rapport à l’heure UTC.  Et les valeurs sérialisées sont toujours désérialisées comme valeurs de date et d’heure locales.  
  
 Vous pouvez utiliser un paramètre de configuration d’application pour déterminer si les <xref:System.Xml.Serialization.XmlSerializer> conserve les informations de fuseau horaire UTC lors de la sérialisation et la désérialisation <xref:System.DateTime> valeurs :  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides   
          value="Switch.System.Runtime.Serialization.DisableSerializeUTCDateTimeToTimeAndDeserializeUTCTimeToUTCDateTime=false" />  
</runtime>  
  
```  
  
 Lorsque cette fonctionnalité est activée, un <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object utilise le <xref:System.TimeZoneInfo> type au lieu de la <xref:System.TimeZone> type pour désérialiser des données de date et d’heure. <xref:System.TimeZoneInfo> prend en charge plusieurs règles d’ajustement, qui permet de manipuler les données historiques de fuseau horaire ;   <xref:System.TimeZone> pas.  
  
 Pour plus d’informations sur la <xref:System.TimeZoneInfo> structure et ajustement de fuseau horaire, consultez [vue d’ensemble du fuseau horaire](../../../docs/standard/datetime/time-zone-overview.md).  
  
 **NetNamedPipeBinding meilleure correspondance**  
 WCF propose un nouveau paramètre d’application qui peut être défini sur les applications clientes de telle sorte qu’elles se connectent systématiquement au service écoutant l’URI qui correspond le mieux à celui qu’elles demandent. Avec ce paramètre d’application défini sur `false` (la valeur par défaut), il est possible pour les clients à l’aide de <xref:System.ServiceModel.NetNamedPipeBinding> pour tenter de se connecter à un service qui écoute sur un URI qui est une sous-chaîne de l’URI demandé.  
  
 Par exemple, un client tente de se connecter à un service à l’écoute de `net.pipe://localhost/Service1`, mais un autre service de cet ordinateur s’exécutant avec des privilèges d’administrateur écoute `net.pipe://localhost`. Si ce paramètre d’application est défini sur `false`, le client tente de se connecter au mauvais service. Une fois le paramètre d’application défini sur `true`, le client se connecte systématiquement au service le plus approprié.  
  
> [!NOTE]
>  Les clients à l’aide de <xref:System.ServiceModel.NetNamedPipeBinding> rechercher des services basés sur l’adresse de base du service (si elle existe) plutôt que l’adresse de point de terminaison complète. Pour faire en sorte que ce paramètre fonctionne toujours, le service doit utiliser une adresse de base unique.  
  
 Pour permettre cette modification, ajoutez le paramètre d’application suivant au fichier App.config ou Web.config de votre application cliente :  
  
```xml  
  
<configuration>  
    <appSettings>  
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />  
    </appSettings>  
</configuration>  
  
```  
  
 **SSL 3.0 n’est pas un protocole par défaut**  
 Quand vous utilisez NetTcp avec la sécurité du transport et un type d’informations d’identification de certificat, SSL 3.0 n’est plus le protocole utilisé par défaut quand il s’agit de négocier une connexion sécurisée. Dans la majorité des cas, cela ne devrait pas avoir de conséquences sur les applications existantes, car TLS 1.0 est inclus dans la liste de protocoles pour NetTcp. Tous les clients existants doivent pouvoir négocier une connexion en utilisant au moins TLS 1.0.      Si Ssl3 est exigé, utilisez l’un des mécanismes de configuration suivants pour l’ajouter à la liste des protocoles négociés.  
  
-   Le <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName> propriété  
  
-   Le <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName> propriété  
  
-   The [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) section of the [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) section  
  
-   The [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) section of the [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) section  
  
<a name="WPF462"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 Dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Presentation Foundation a été amélioré dans les domaines suivants :  
  
 **Tri des groupes**  
 Une application qui utilise un <xref:System.Windows.Data.CollectionView> objet pour regrouper les données permettre déclarer maintenant explicitement comment trier les groupes. Le tri explicite résout le problème du classement non intuitif qui se produit quand une application ajoute ou supprime dynamiquement des groupes ou quand elle modifie la valeur de propriétés d’élément impliquées dans le regroupement. Il peut aussi améliorer l’efficacité de la création de groupes en comparant les propriétés de regroupement non pas au niveau du tri de la collection complète mais du tri des groupes.  
  
 Pour prendre en charge le tri des groupes, la nouvelle <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=fullName> et <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=fullName> propriétés décrivent comment effectuer un tri de la collection de groupes de produits par le <xref:System.ComponentModel.GroupDescription> objet. Ce comportement est similaire à celle portant le même nom <xref:System.Windows.Data.ListCollectionView> propriétés décrivent comment trier les éléments de données.  
  
 Deux nouvelles propriétés statiques de la <xref:System.Windows.Data.PropertyGroupDescription> (classe), <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> et <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, peut être utilisé pour les scénarios les plus courants.  
  
 Par exemple, le code XAML suivant regroupe les données par âge, trie les groupes d’âge par ordre croissant, puis regroupe les éléments de chaque groupe d’âge par nom de famille.  
  
```xaml  
  
<GroupDescriptions>  
     <PropertyGroupDescription   
         PropertyName=”Age”   
         CustomSort=   
              ”{x:Static PropertyGroupDescription.CompareNamesAscending}”/>  
     </PropertyGroupDescription>  
</GroupDescriptions>  
  
<SortDescriptions>  
     <SortDescription PropertyName=”LastName”/>  
</SortDescriptions>  
  
```  
  
 **Prise en charge de clavier programmable**  
 La prise en charge des claviers logiciels permet d’assurer le suivi du focus dans les applications WPF en appelant et en masquant automatiquement le nouveau clavier logiciel dans Windows 10 dès lors que l’entrée tactile est reçue par un contrôle qui peut prendre l’entrée textuelle.  
  
 Dans les versions précédentes du .NET Framework, les applications WPF ne peuvent pas opter pour le suivi du focus sans désactiver la prise en charge du stylo et des entrées tactiles WPF.  Par conséquent, les applications WPF doivent soit choisir la prise en charge complète des entrées tactiles WPF, soit privilégier la souris Windows.  
  
 **Résolution d’écran**  
 Pour faire face à la prolifération récente des environnements à haute résolution et à résolution hybride pour les applications WPF, WPF dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] autorise une prise en charge par moniteur. Consultez le [exemples et le guide du développeur](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) sur GitHub pour plus d’informations sur l’activation de votre application WPF de devenir par moniteur PPP prenant en charge.  
  
 Dans les versions précédentes du .NET Framework, les applications WPF prennent en charge la résolution au niveau du système. En d’autres termes, l’interface utilisateur de l’application est éventuellement mise à l’échelle par le système d’exploitation, en fonction de la résolution du moniteur sur lequel l’application est affichée. ,  
  
 Pour les applications s’exécutant sous le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], vous pouvez désactiver les modifications PPP d’analyse dans les applications WPF en ajoutant une instruction de configuration pour le [ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) fichier de section de configuration de votre application, comme suit :  
  
```xml  
  
<runtime>  
   <AppContextSwitchOverrides value=”Switch.System.Windows.DoNotScaleForDpiChanges=false”/>  
</runtime>  
  
```  
  
<a name="WF462"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 Dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Workflow Foundation a été amélioré dans les domaines suivants :  
  
 **Prise en charge d’IntelliSense dans le concepteur WF Re-hosted et les expressions c#**  
 À compter du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], WF prend en charge les expressions C# dans le concepteur de Visual Studio et dans les flux de travail de code. Le Concepteur de flux de travail réhébergé est une fonctionnalité clé de WF qui autorise la présence du Concepteur de flux de travail dans une application extérieure à Visual Studio (par exemple, dans WPF).  Windows Workflow Foundation permet de prendre en charge les expressions C# et IntelliSense dans le Concepteur de flux de travail réhébergé. Pour plus d’informations, consultez la [blog de Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409).  
  
 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`  
 Dans les versions du .NET Framework antérieures au [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], la fonctionnalité IntelliSense du Concepteur de flux de travail est inopérante quand un client reconstruit un projet de flux de travail à partir de Visual Studio. Pendant la génération du projet réussit, les types de flux de travail ne se trouvent pas sur le concepteur et avertissements d’IntelliSense pour les types de flux de travail manquant s’affichent dans le **liste d’erreurs** fenêtre. Le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] résout ce problème et donne accès à IntelliSense.  
  
 **Applications V1 de flux de travail avec les flux de travail de suivi en cours s’exécuter en mode FIPS**  
 Les ordinateurs pour lesquels le mode de conformité FIPS est activé peuvent désormais exécuter correctement une application de type Workflow version 1 en ayant le suivi de flux de travail activé. Pour permettre ce cas de figure, vous devez apporter la modification suivante à votre fichier app.config :  
  
```xml  
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />  
```  
  
 Si ce scénario n’est pas autorisé, l’exécution de l’application continue de générer une exception avec le message « Cette implémentation ne fait pas partie des algorithmes de chiffrement validés FIPS pour les plateformes Windows ».  
  
 **Améliorations des flux de travail lors de l’utilisation de la mise à jour dynamique avec le Concepteur de flux de travail Visual Studio**  
 Le Concepteur de flux de travail, Concepteur d’activité d’organigramme et d’autres concepteurs d’activités de flux de travail maintenant correctement charger et afficher des flux de travail qui ont été enregistrés après avoir appelé la <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=fullName> (méthode). Dans les versions du .NET Framework avant le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], le chargement d’un fichier XAML dans Visual Studio pour un flux de travail qui a été enregistré après avoir appelé <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=fullName> peut entraîner les problèmes suivants :  
  
-   Le Concepteur de Workflow ne peut pas charger le fichier XAML correctement (lorsque le <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=fullName> est à la fin de la ligne).  
  
-   Le Concepteur d’activités d’organigramme ou les autres Concepteurs d’activités de flux de travail peuvent afficher tous les objets à leurs emplacements par défaut plutôt que les valeurs de propriétés jointes.  
  
<a name="ClickOnce"></a>   
### <a name="clickonce"></a>ClickOnce  
 ClickOnce a été mis à jour pour prendre en charge TLS 1.1 et TLS 1.2 en plus du protocole 1.0, qu’il prend déjà en charge. ClickOnce détecte automatiquement le protocole exigé ; aucune mesure supplémentaire n’est à prendre dans l’application ClickOnce pour activer la prise en charge de TLS 1.1 et 1.2.  
  
<a name="UWPConvert"></a>   
### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Conversion des Windows Forms et des applications WPF en applications UWP  
 Windows permet désormais de porter les applications de bureau Windows, dont les applications WPF et Windows Forms, sur la plateforme Windows universelle (UWP). Cette technologie fait office de pont en vous permettant de migrer progressivement votre base de code existante vers UWP, et ainsi de porter votre application sur tous les appareils Windows 10.  
  
 Les applications de bureau converties obtiennent une identité d’application comparable à celle des applications UWP, ce qui rend les API UWP accessibles pour activer certaines fonctionnalités, telles que les vignettes dynamiques et les notifications. L’application continue de se comporter comme auparavant et s’exécute comme une application entièrement approuvée. Une fois l’application convertie, un processus de conteneur d’application peut être ajouté au processus d’approbation complète existant pour ajouter une interface utilisateur adaptative. Quand toutes les fonctionnalités sont déplacées vers le processus de conteneur d’application, le processus d’approbation complète peut être supprimé et la nouvelle application UWP peut être mise à la disposition de tous les appareils Windows 10.  
  
<a name="Debug462"></a>   
### <a name="debugging-improvements"></a>Améliorations du débogage  
 Le *API de débogage non managé* a été améliorée dans le [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] pour effectuer des analyses supplémentaires lorsqu’un <xref:System.NullReferenceException> levée afin qu’il soit possible de déterminer quelle variable dans une seule ligne de code source est `null`.   Pour favoriser ce scénario, les API ci-dessous ont été ajoutées à l’API de débogage non managé.  
  
-   Le [ICorDebugCode4](../../../ocs/framework/unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../../../ocs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md), et [ICorDebugVariableHomeEnum](../../../ocs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interfaces, qui exposent les maisons natifs variables gérées. Cela permet aux débogueurs effectuer des analyses de flux de code lorsqu’un <xref:System.NullReferenceException> se produit et revenir en arrière pour déterminer la variable managée qui correspond à l’emplacement natif a été `null`.  
  
-   Le [ICorDebugType2::GetTypeID](../Topic/ICorDebugType2::GetTypeID%20Method.md) méthode fournit un mappage ICorDebugType à [COR_TYPEID](../../../ocs/framework/unmanaged-api/debugging/cor-typeid-structure.md), ce qui permet au débogueur d’obtenir un [COR_TYPEID](../../../ocs/framework/unmanaged-api/debugging/cor-typeid-structure.md) sans une instance de la ICorDebugType. Les API existantes sur [COR_TYPEID](../../../ocs/framework/unmanaged-api/debugging/cor-typeid-structure.md) peut ensuite servir à déterminer la disposition de classe du type.  
  
<a name="v461"></a>   
## <a name="whats-new-in-the-net-framework-461"></a>Nouveautés dans le .NET Framework 4.6.1  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] inclut de nouvelles fonctionnalités dans les domaines suivants :  
  
-   [Cryptographie](#Crypto)  
  
-   [ADO.NET](#ADO.NET461)  
  
-   [Windows Presentation Foundation (WPF)](#WPF461)  
  
-   [Windows Workflow Foundation](#WWF461)  
  
-   [Le profilage](#Profile461)  
  
-   [NGen](#NGEN461)  
  
 Pour plus d’informations sur [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], consultez les rubriques suivantes :  
  
-   Le [liste .NET Framework 4.6.1 des modifications](http://go.microsoft.com/fwlink/?LinkId=622964)  
  
-   [Compatibilité des applications dans 4.6.1](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)  
  
-   [La comparaison des API .NET Framework](http://go.microsoft.com/fwlink/?LinkId=622989) (sur GitHub)  
  
<a name="Crypto"></a>   
### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Chiffrement : prise en charge des certificats X509 contenant l’algorithme ECDSA  
 .NET Framework 4.6 a ajouté la prise en charge de l’algorithme RSACng pour les certificats X509. [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ajoute la prise en charge des certificats X509 ECDSA (Elliptic Curve Digital Signature Algorithm).  
  
 ECDSA offre de meilleures performances et constitue un algorithme de chiffrement plus sécurisé que RSA. Il constitue un excellent choix quand les performances et la scalabilité de la sécurité de la couche de transport (TLS) constituent une préoccupation. L’implémentation du .NET Framework encapsule les appels dans les fonctionnalités Windows existantes.  
  
 L’exemple de code suivant montre combien il est facile de générer une signature pour un flux d’octets à l’aide de la nouvelle prise en charge des certificats X509 ECDSA inclus dans [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 [!code-csharp[whatsnew.461.crypto#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
 [!code-vb[whatsnew.461.crypto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]  
  
 Cela contraste fortement avec le code nécessaire pour générer une signature dans .NET Framework 4.6.  
  
 [!code-csharp[whatsnew.461.crypto#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
 [!code-vb[whatsnew.461.crypto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]  
  
<a name="ADO.NET461"></a>   
### <a name="adonet"></a>ADO.NET  
 Les éléments suivants ont été ajoutés à ADO.NET :  
  
 Prise en charge de la fonctionnalité Chiffrement intégral pour les clés matérielles protégées  
 ADO.NET prend désormais en charge le stockage des clés principales de colonnes Toujours chiffré en mode natif dans les modules de sécurité matériels (HSM, Hardware Security Modules). Cette prise en charge permet aux clients de tirer profit des clés asymétriques stockées dans les modules HSM sans avoir à écrire des fournisseurs de magasins de clés principales de colonnes personnalisés et sans les inscrire dans les applications.  
  
 Les clients doivent installer le fournisseur CSP fourni par le fabricant des modules HSM ou les fournisseurs de magasin de clés CNG sur les serveurs d’applications ou les ordinateurs clients pour accéder aux données Toujours chiffré protégées par des clés principales de colonnes stockées dans un module HSM.  
  
 Améliorer les <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> comportement de connexion pour AlwaysOn  
 Désormais, SqlClient fournit automatiquement une connexion plus rapide à un groupe de disponibilité AlwaysOn (AG, Availability Group). Il détecte de façon transparente si votre application se connecte à un groupe de disponibilité AlwaysOn sur un autre sous-réseau, détecte rapidement le serveur actif actuel et fournit une connexion au serveur. Avant cette mise en production, une application devait définir la chaîne de connexion à inclure `“MultisubnetFailover=true”` pour indiquer qu’elle était connectée à un groupe de disponibilité AlwaysOn. Si le mot clé de connexion n’était pas défini sur `true`, une application pouvait rencontrer un dépassement du délai lors de la connexion à un groupe de disponibilité AlwaysOn. Avec cette version, une application effectue *pas* devez définir <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> à `true` plus. Pour plus d’informations sur la prise en charge de SqlClient pour les groupes de disponibilité AlwaysOn, consultez [prise en charge de SqlClient pour la haute disponibilité, récupération d’urgence](../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).  
  
<a name="WPF461"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 Windows Presentation Foundation inclut un certain nombre d’améliorations et de modifications.  
  
 Performances améliorées  
 Le retard de déclenchement d’événements tactiles a été résolu dans [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. En outre, en tapant dans une <xref:System.Windows.Controls.RichTextBox> contrôle n’est plus s’associe le thread de rendu au cours de l’entrée rapide.  
  
 Améliorations de la vérification orthographique  
 Le vérificateur orthographique de WPF a été mis à jour sur Windows 8.1 et les versions ultérieures pour tirer parti de la prise en charge, par le système d’exploitation, de la vérification orthographique de langues supplémentaires.  Aucune fonctionnalité n’a été modifiée sur les versions de Windows antérieures à Windows 8.1.  
  
 Comme dans les versions précédentes du .NET Framework, la langue pour une <xref:System.Windows.Controls.TextBox> contrôle ora <xref:System.Windows.Controls.RichTextBox> bloc est détecté en recherchant des informations dans l’ordre suivant :  
  
-   `xml:lang`, le cas échéant.  
  
-   Langue d’entrée actuelle.  
  
-   Culture de thread actuelle.  
  
 Pour plus d’informations sur la prise en charge linguistique dans WPF, consultez la [billet de blog WPF sur les fonctionnalités de .NET Framework 4.6.1](http://go.microsoft.com/fwlink/?LinkID=691819).  
  
 Prise en charge supplémentaire des dictionnaires personnalisés par utilisateur  
 Dans [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], WPF reconnaît les dictionnaires personnalisés qui sont inscrits de manière globale. Cette fonctionnalité est disponible en plus de la possibilité de les inscrire par contrôle.  
  
 Dans les versions précédentes de WPF, les dictionnaires personnalisés ne reconnaissaient pas les listes Mots exclus et Correction automatique. Ils sont pris en charge sur Windows 8.1 et Windows 10 via l’utilisation de fichiers qui peuvent être placés sous le répertoire `%AppData%\Microsoft\Spelling\<language tag>`.  Les règles suivantes s’appliquent à ces fichiers :  
  
-   Les fichiers doivent avoir l’extension .dic (pour les mots ajoutés), .exc (pour les mots exclus) ou .acl (pour la correction automatique).  
  
-   Les fichiers doivent être en texte brut UTF-16 LE qui commence par la marque d’ordre d’octet.  
  
-   Chaque ligne doit être constitué d’un mot (dans les listes de mots exclus et ajouté) ou une paire de correction automatique avec les mots séparés par une barre verticale (« | ») (dans la liste de mots de correction automatique).  
  
-   Ces fichiers sont considérés en lecture seule et ne sont pas modifiés par le système.  
  
> [!NOTE]
>  Ces nouveaux formats de fichier ne sont pas directement pris en charge par les API de correction orthographique WPF, et les dictionnaires personnalisés fournis à WPF dans les applications doivent continuer à utiliser les fichiers .lex.  
  
 Exemples  
 Il existe un certain nombre de [exemples WPF](https://msdn.microsoft.com/library/ms771633.aspx) sur MSDN. Plus de 200 échantillons plus populaires (en fonction de leur utilisation) sera déplacé vers un [référentiel Open Source GitHub](https://github.com/Microsoft/WPF-Samples). Aidez-nous à améliorer nos exemples en nous envoyant une requête d’extraction ou d’une ouverture un [GitHub problème](https://github.com/Microsoft/WPF-Samples/issues).  
  
 Extensions DirectX  
 WPF inclut une [package NuGet](http://go.microsoft.com/fwlink/?LinkID=691342) qui fournit de nouvelles implémentations de <xref:System.Windows.Interop.D3DImage> qui facilitent vous permet d’interagir avec DX10 et Dx11 contenu. Le code pour ce package a été ouvert alimenté et est disponible [sur GitHub](https://github.com/Microsoft/WPFDXInterop).  
  
<a name="WWF461"></a>   
### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation : Transactions  
 Le <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=fullName> méthode peut maintenant utiliser un gestionnaire de transactions distribuées que MSDTC pour promouvoir la transaction. Cela en spécifiant l’identificateur GUID transaction promoteur au nouveau <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=fullName> de surcharge. Si cette opération réussit, des limitations sont placées sur les fonctionnalités de la transaction. Une fois qu’un promoteur de transaction non MSDTC est inscrite, les méthodes suivantes lèvent une <xref:System.Transactions.TransactionPromotionException> , car ces méthodes requièrent la promotion à MSDTC :  
  
-   <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=fullName>  
  
-   <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=fullName>  
  
-   <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=fullName>  
  
-   <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=fullName>  
  
 Une fois qu’un promoteur de transaction non MSDTC est inscrit, il doit être utilisé pour les futures inscriptions durables en utilisant les protocoles qu’il définit. Le <xref:System.Guid> de la transaction promoteur peut être obtenu à l’aide de la <xref:System.Transactions.Transaction.PromoterType%2A> propriété. Lorsque la transaction promeut, promoteur transaction fournit un <xref:System.Byte> tableau qui représente le jeton promu. Une application peut obtenir le jeton promu pour une transaction MSDTC-non promu avec le <xref:System.Transactions.Transaction.GetPromotedToken%2A> (méthode).  
  
 Les utilisateurs de la nouvelle <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=fullName> surcharge doit suivre une séquence d’appel spécifiques afin que l’opération de promotion terminer avec succès. Ces règles sont documentées dans la documentation de la méthode.  
  
<a name="Profile461"></a>   
### <a name="profiling"></a>Profilage  
 L’API de profilage non managée a été améliorée comme suit :  
  
 Meilleure prise en charge pour l’accès aux fichiers PDB dans le [ICorProfilerInfo7](../../../ocs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface  
 Dans ASP.Net 5, la compilation des assemblys en mémoire par Roslyn est beaucoup plus courante. Pour les développeurs qui créent des outils de profilage, cela signifie que les fichiers PDB qui étaient historiquement sérialisés sur le disque risquent de ne plus être présents. Les outils de profilage utilisent souvent des fichiers PDB pour remapper du code aux lignes sources pour des tâches telles que la couverture du code ou l’analyse des performances ligne par ligne. Le [ICorProfilerInfo7](../../../ocs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface inclut maintenant deux nouvelles méthodes, [ICorProfilerInfo7::GetInMemorySymbolsLength](../Topic/ICorProfilerInfo7::GetInMemorySymbolsLength%20Method.md) et [ICorProfilerInfo7::ReadInMemorySymbols](../Topic/ICorProfilerInfo7::ReadInMemorySymbols.md), pour les outils de profilage fournissent un accès aux données PDB en mémoire, en utilisant les nouvelles API, un profileur peut obtenir le contenu d’un fichier PDB en mémoire comme un tableau d’octets et puis la traiter ou sa sérialisation sur le disque.  
  
 Meilleure instrumentation avec l’interface ICorProfiler  
 Les profileurs qui utilisent la fonctionnalité ReJit de l’API `ICorProfiler` pour l’instrumentation dynamique peuvent maintenant modifier certaines métadonnées. Précédemment, ces outils pouvaient instrumenter le langage intermédiaire à tout moment, mais les métadonnées ne pouvaient être modifiées qu’au moment du chargement du module. Étant donné que le langage intermédiaire fait référence aux métadonnées, cela limitait les types d’instrumentation qui pouvaient être effectuées. Nous avons levé à certaines de ces limites en ajoutant le [ICorProfilerInfo7::ApplyMetaData](../Topic/ICorProfilerInfo7::ApplyMetaData%20Method.md) méthode pour prendre en charge un sous-ensemble des modifications de métadonnées une fois que le module se charge, notamment en ajoutant de nouveaux `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, et `UserString` enregistrements. Cette modification permet une plus large gamme d’instrumentations instantanées possibles.  
  
<a name="NGEN461"></a>   
### <a name="native-image-generator-ngen-pdbs"></a>Fichiers PDB du générateur d’images natives (NGen)  
 Le suivi d’événements entre ordinateurs permet aux clients de profiler un programme sur l’Ordinateur A et d’examiner les données de profilage avec le mappage des lignes sources sur l’Ordinateur B. Avec les versions antérieures du .NET Framework, l’utilisateur devait copier tous les modules et les images natives de l’ordinateur profilé vers l’ordinateur d’analyse qui contenait le fichier PDB en langage intermédiaire pour créer le mappage du code source au code natif. Ce processus peut fonctionner correctement lorsque les fichiers sont relativement petits, comme pour les applications de téléphone. Toutefois, les fichiers peuvent être très volumineux sur des systèmes de bureau et leur copie peut prendre beaucoup de temps.  
  
 Avec les fichiers PDB de NGen, NGen peut créer un fichier PDB qui contient le mappage du langage intermédiaire au code natif sans dépendance sur le fichier PDB en langage intermédiaire. Dans notre scénario de suivi des événements de plusieurs ordinateurs, tout ce qui est nécessaire est de copier l’image native PDB généré par un ordinateur à l’ordinateur B et d’utiliser [Debug Interface Access API](https://msdn.microsoft.com/en-us/library/ee8x173s.aspx) pour lire le mappage de source-à-IL du PDB langage intermédiaire et mappage de langage intermédiaire – natif le PDB image native. La combinaison des deux mappages fournit un mappage du code source au code natif. Étant donné que le fichier PDB de l’image native est beaucoup plus petit que l’ensemble des modules et images natives, le processus de copie de l’Ordinateur A vers l’Ordinateur B est beaucoup plus rapide.  
  
<a name="v46"></a>   
## <a name="whats-new-in-net-2015"></a>Nouveautés du .NET 2015  
 .NET 2015 introduit le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] et .NET Core. Certaines nouvelles fonctionnalités s'appliquent aux deux infrastructures, alors que d'autres sont spécifiques à [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ou [!INCLUDE[net_core](../../../includes/net-core-md.md)].  
  
-   **ASP.NET 5**  
  
     .NET 2015 inclut ASP.NET 5, qui est une plateforme .NET pour la création d'applications cloud modernes. La plateforme est modulaire, ce qui vous permet d'inclure uniquement les fonctionnalités nécessaires dans votre application. Elle peut être hébergée sur IIS ou auto-hébergée dans un processus personnalisé. Par ailleurs, vous pouvez exécuter les applications avec différentes versions du .NET Framework sur le même serveur. Elle inclut un nouveau système de configuration d'environnement conçu pour le déploiement cloud.  
  
     MVC, les API web et les pages web sont unifiés dans une infrastructure unique appelée MVC 6. Vous créez des applications ASP.NET 5 via les nouveaux outils de Visual Studio 2015. Vos applications existantes fonctionneront sur le nouveau .NET Framework. Toutefois, pour générer une application qui utilise MVC 6 ou SignalR 3, vous devez utiliser le système de projet de Visual Studio 2015.  
  
     Pour plus d’informations, consultez [ASP.NET 5](http://go.microsoft.com/fwlink/?LinkId=518238).  
  
-   **Mises à jour ASP.NET**  
  
    -   **API de tâche pour le vidage de réponse asynchrone**  
  
         ASP.NET fournit désormais une API simple basée sur les tâches de vidage de la réponse asynchrone, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=fullName>, qui autorise les réponses de vidage asynchrone à l’aide de votre langage `async/await` prennent en charge.  
  
    -   `Model binding supports task-returning methods`  
  
         Dans le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ASP.NET a ajouté une fonctionnalité de liaison de modèle qui autorise une approche extensible, axée sur le code pour les opérations de données CRUD dans les contrôles utilisateur et les pages Web Forms. Le système de liaison de modèle prend désormais en charge <xref:System.Threading.Tasks.Task>-retour de méthodes de liaison de modèle. Cette fonctionnalité permet aux développeurs de Web Forms d'obtenir les avantages de la scalabilité du modèle asynchrone et la simplicité du système de liaison de données lorsqu'ils utilisent les versions plus récentes des ORM, y compris l'Entity Framework.  
  
         La liaison de modèle asynchrone est contrôlée par le paramètre de configuration `aspnet:EnableAsyncModelBinding`.  
  
        ```  
  
        <appSettings>  
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />  
        </appSettings>  
  
        ```  
  
         Sur les applications qui ciblent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], sa valeur par défaut est `true`. Sur les applications s'exécutant sur le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] qui ciblent une version antérieure du .NET Framework, sa valeur par défaut est `false`. Son activation s'obtient en définissant le paramètre de configuration avec la valeur `true`.  
  
    -   **Prise en charge HTTP/2 (Windows 10)**  
  
         [HTTP/2](http://www.wikipedia.org/wiki/HTTP/2) est une nouvelle version du protocole HTTP qui offre une bien meilleure utilisation de la connexion (moins d’allers-retours entre le client et serveur), ce qui réduit la latence des pages web de chargement pour les utilisateurs.  Ce sont les pages web (par opposition aux services) qui profitent le plus de HTTP/2, car le protocole optimise les demandes de plusieurs artefacts dans une expérience unique. La prise en charge de HTTP/2 a été ajoutée à ASP.NET dans le .NET Framework 4.6. Étant donné que les fonctionnalités réseau existent sur plusieurs couches, de nouvelles fonctionnalités ont dû être rajoutées dans Windows, IIS et ASP.NET pour activer HTTP/2. Vous devez exécuter Windows 10 pour utiliser HTTP/2 avec ASP.NET.  
  
         HTTP/2 est également pris en charge et sur par défaut, pour Windows 10 Universal Windows Platform (UWP) des applications qui utilisent la <xref:System.Net.Http.HttpClient?displayProperty=fullName> API.  
  
         Afin de fournir un moyen d’utiliser la [PUSH_PROMISE](http://http2.github.io/http2-spec/#PUSH_PROMISE) des fonctionnalités dans les applications ASP.NET, une méthode avec deux surcharges, <xref:System.Web.HttpResponse.PushPromise%28System.String%29> et <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, a été ajouté à la <xref:System.Web.HttpResponse> classe.  
  
        > [!NOTE]
        >  Alors qu’ASP.NET 5 prend en charge HTTP/2, la prise en charge de la fonctionnalité PUSH PROMISE n’a pas encore été ajoutée.  
  
         Le navigateur et le serveur web (IIS sur Windows) effectuent tout le travail. Vous n'avez pas de tâches lourdes à effectuer pour vos utilisateurs.  
  
         La plupart de la [principaux navigateurs prennent en charge HTTP/2](http://www.wikipedia.org/wiki/HTTP/2), il est donc probable que vos utilisateurs bénéficient de la prise en charge HTTP/2 si votre serveur prend en charge.  
  
    -   **Prise en charge pour le protocole de liaison de jeton**  
  
         Microsoft et Google ont collaboré sur une nouvelle approche de l’authentification, appelée la [protocole de liaison de jeton](https://github.com/TokenBinding/Internet-Drafts). Le principe est que les jetons d’authentification (dans le cache de votre navigateur) peuvent être volés et utilisés par des personnes mal intentionnées pour accéder aux ressources sécurisées dans le cas contraire (par exemple, votre compte bancaire) sans votre mot de passe ou toute autre information confidentielle. Le nouveau protocole vise à contenir ce problème.  
  
         Le protocole de liaison de jeton sera implémenté dans Windows 10 en tant que fonctionnalité du navigateur. Les applications ASP.NET participeront au protocole, en validant les jetons d'authentification pour qu'ils soient légitimes. Les implémentations côté client et serveur établissent la protection de bout en bout spécifiée par le protocole.  
  
    -   **Algorithmes de hachage de chaîne aléatoire**  
  
         Le .NET Framework 4.5 introduit un [algorithme de hachage de chaîne aléatoire](https://msdn.microsoft.com/library/jj152924.aspx). Cependant, il n'est pas pris en charge par ASP.NET en raison de certaines fonctionnalités ASP.NET fondées sur un code de hachage stable. Dans [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], les algorithmes de hachage de chaîne aléatoire sont désormais pris en charge. Pour activer cette fonctionnalité, utilisez le paramètre de configuration `aspnet:UseRandomizedStringHashAlgorithm`.  
  
        ```  
  
        <appSettings>  
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />  
        </appSettings>  
  
        ```  
  
-   **ADO.NET**  
  
     ADO .NET prend désormais en charge la fonctionnalité Toujours chiffré disponible dans SQL Server 2016 version préliminaire CTP2 (Community Technology Preview 2). Avec la fonctionnalité Toujours chiffré, SQL Server peut effectuer des opérations sur des données chiffrées, et surtout, la clé de chiffrement est stockée avec l'application à l'intérieur de l'environnement approuvé du client, et non pas sur le serveur. La fonctionnalité Toujours chiffré sécurise les données du client de sorte que les administrateurs de base de données n'ont pas accès aux données en texte brut. Le chiffrement et le déchiffrement de données se produit de manière transparente au niveau du pilote, ce qui réduit des modifications à apporter aux applications existantes. Pour plus d’informations, consultez [toujours chiffrées (moteur de base de données)](https://msdn.microsoft.com/library/mt163865\(v=sql.130\).aspx) et [toujours chiffrées (développement client)](https://msdn.microsoft.com/library/mt147923\(v=sql.130\).aspx).  
  
-   **Compilateur JIT de&64; bits pour le code managé**  
  
     Le .NET Framework 4.6 propose une nouvelle version du compilateur JIT 64 bits (anciennement RyuJIT). Le nouveau compilateur 64 bits offre des améliorations significatives des performances par rapport à l'ancien compilateur JIT 64 bits. Le nouveau compilateur 64 bits est activé pour les processus 64 bits qui s'exécutent au-dessus du .NET Framework 4.6. Votre application s'exécute dans un processus 64 bits s'il est compilé en mode 64 bits ou AnyCPU, et s'exécute sur un système d'exploitation 64 bits. Bien que toutes les mesures nécessaires aient été prises pour que la transition vers le nouveau compilateur soit aussi transparente que possible, des modifications du comportement sont possibles. Nous aimerions connaître directement les problèmes que vous pourriez rencontrer lorsque vous utilisez le nouveau compilateur JIT. Veuillez nous contacter via [Microsoft Connect](http://connect.microsoft.com/) si vous rencontrez un problème qui peut être lié au nouveau compilateur JIT 64 bits.  
  
     Le nouveau compilateur JIT 64 bits inclut également des fonctionnalités d’accélération matérielle SIMD lorsqu’il est combiné avec des types compatibles SIMD dans le <xref:System.Numerics> espace de noms, qui peut produire des améliorations de bonnes performances.  
  
-   **Améliorations du chargeur d’assembly**  
  
     Le chargeur d'assembly utilise désormais la mémoire plus efficacement en déchargeant les assemblys IL après le chargement d'une image NGEN correspondante. Cette modification réduit la mémoire virtuelle, ce qui est particulièrement utile pour les grandes applications 32 bits (tels que Visual Studio), et économise aussi la mémoire physique.  
  
-   **Changements de bibliothèque de classes de base**  
  
     Plusieurs nouvelles API ont été ajoutées à [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] pour des scénarios clés. Vous remarquerez les changements et les ajouts suivants :  
  
    -   **IReadOnlyCollection<> \</> \> mises en œuvre**  
  
         Des collections supplémentaires implémentent <xref:System.Collections.Generic.IReadOnlyCollection%601> comme <xref:System.Collections.Generic.Queue%601> et <xref:System.Collections.Generic.Stack%601>.  
  
    -   **CultureInfo.CurrentCulture et CultureInfo.CurrentUICulture**  
  
         Le <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> et <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> sont désormais des propriétés en lecture-écriture et non en lecture seule. Si vous affectez un nouvel <xref:System.Globalization.CultureInfo> objet pour ces propriétés, la culture du thread actuel définie par le `Thread.CurrentThread.CurrentCulture` propriété et l’interface utilisateur actuelle du thread culture définie par le `Thread.CurrentThread.CurrentUICulture` également modifier les propriétés.  
  
    -   **Améliorations apportées au garbage collection (GC)**  
  
         Le <xref:System.GC> classe inclut désormais <xref:System.GC.TryStartNoGCRegion%2A> et <xref:System.GC.EndNoGCRegion%2A> des méthodes qui vous permettent d’interdire le garbage collection pendant l’exécution d’un chemin d’accès critique.  
  
         Une nouvelle surcharge de la <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=fullName> méthode vous permet de contrôler si le tas de petits objets et le tas d’objets volumineux sont rangés et compactés ou rangés uniquement.  
  
    -   **Types compatibles SIMD**  
  
         Le <xref:System.Numerics> espace de noms inclut désormais un nombre de types compatibles SIMD, telles que <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, et <xref:System.Numerics.Vector4>.  
  
         Comme le nouveau compilateur JIT 64 bits inclut également des fonctionnalités d'accélération matérielle SIMD, il en découle une amélioration des performances particulièrement significative lorsque vous utilisez les types SIMD avec le nouveau compilateur JIT 64 bits.  
  
    -   **Mises à jour de la cryptographie**  
  
         Le <xref:System.Security.Cryptography?displayProperty=fullName> API est mis à jour pour prendre en charge les [API de chiffrement CNG de Windows](https://msdn.microsoft.com/library/windows/desktop/aa376214.aspx). Des versions précédentes du .NET Framework reposent entièrement sur un [version antérieure de l’API de chiffrement Windows](https://msdn.microsoft.com/library/windows/desktop/aa380255.aspx) comme base pour le <xref:System.Security.Cryptography?displayProperty=fullName> implémentation. Nous avons reçu des demandes pour prendre en charge l’API CNG, car il prend en charge [les algorithmes de chiffrement moderne](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx#suite_b_support), qui sont importants pour certaines catégories d’applications.  
  
         Le .NET Framework 4.6 inclut les améliorations suivantes pour prendre en charge l'API de chiffrement CNG de Windows :  
  
        -   Un ensemble de méthodes d'extension pour les certificats X509, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` et `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, qui retourne une implémentation CNG plutôt qu'une implémentation CAPI lorsque cela est possible. (Certaines cartes à puce, etc., nécessitent toujours CAPI, et les API gèrent le secours).  
  
        -   Le <xref:System.Security.Cryptography.RSACng?displayProperty=fullName> (classe), qui fournit une implémentation CNG de l’algorithme RSA.  
  
        -   Améliorations apportées à l'API RSA afin que les opérations courantes ne nécessitent plus de conversion. Par exemple, le chiffrement des données à l’aide un <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> objet nécessite le code comme suit dans les versions antérieures du .NET Framework.  
  
             [!code-csharp[WhatsNew.Casting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
             [!code-vb[WhatsNew.Casting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]  
  
             Le code qui utilise les nouvelles API de chiffrement dans le .NET Framework 4.6 peut être réécrit comme suit pour éviter la conversion.  
  
             [!code-csharp[WhatsNew.Casting#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
             [!code-vb[WhatsNew.Casting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]  
  
    -   **Prise en charge pour la conversion des dates et heures vers ou à partir de l’heure Unix**  
  
         Les nouvelles méthodes suivantes ont été ajoutées à la <xref:System.DateTimeOffset> structure pour prendre en charge la conversion des valeurs de date et d’heure vers ou à partir de Unix :  
  
        -   <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=fullName>  
  
        -   <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=fullName>  
  
        -   <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=fullName>  
  
        -   <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=fullName>  
  
    -   **Commutateurs de compatibilité**  
  
         La nouvelle <xref:System.AppContext> classe ajoute une nouvelle fonctionnalité de compatibilité qui permet aux auteurs de bibliothèque fournir un mécanisme d’annulations uniforme des nouvelles fonctionnalités pour leurs utilisateurs. Elle établit un contrat souple entre les composants pour la communication des demandes de désactivation. Cette fonctionnalité est particulièrement importante quand une modification est apportée aux fonctionnalités existantes. À l'inverse, il existe déjà une activation implicite des nouvelles fonctionnalités.  
  
         Avec <xref:System.AppContext>, les bibliothèques définissent et exposent des commutateurs de compatibilité, tandis que le code qui en dépend peuvent définir ces commutateurs pour affecter le comportement de la bibliothèque. Par défaut, les bibliothèques fournissent la nouvelle fonctionnalité et ne peuvent la modifier (c'est-à-dire fournir la version antérieure) que si le commutateur est défini.  
  
         Une application (ou une bibliothèque) peut déclarer la valeur d’un commutateur (qui est toujours un <xref:System.Boolean> valeur) qui définit une bibliothèque dépendante. Le commutateur a toujours implicitement la valeur `false`. En définissant le commutateur avec la valeur `true`, vous l'activez. En définissant explicitement le commutateur avec la valeur `false`, vous obtenez le nouveau comportement.  
  
        ```csharp  
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);  
        ```  
  
         La bibliothèque doit vérifier si un consommateur a déclaré la valeur du commutateur et s'il l'utilise ensuite correctement.  
  
        ```  
  
        if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow))   
        {  
           // This is the case where the switch value was not set by the application.   
           // The library can choose to get the value of shouldThrow by other means.   
           // If no overrides nor default values are specified, the value should be 'false'.   
           // A false value implies the latest behavior.  
        }  
  
           // The library can use the value of shouldThrow to throw exceptions or not.  
           if (shouldThrow)   
           {  
              // old code  
           }  
           else {  
              // new code  
           }  
        }  
  
        ```  
  
         Il est préférable d'utiliser un format homogène pour les commutateurs, car ils constituent un contrat formel exposé par une bibliothèque. Voici les deux formats évidents.  
  
        -   *Switch*.* espace de noms*.* SwitchName*  
  
        -   *Switch*.* library*.* SwitchName*  
  
    -   **Modifications du modèle asynchrone basé sur les tâches (TAP)**  
  
         Pour les applications qui ciblent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> objets héritent de la culture et la culture d’interface utilisateur du thread appelant. Le comportement des applications qui ciblent les versions antérieures du .NET Framework, ou qui ne ciblent pas une version spécifique du .NET Framework n'est pas affecté. Pour plus d’informations, consultez la section « Culture et opérations asynchrones basées sur des tâches » de la <xref:System.Globalization.CultureInfo> rubrique de la classe.  
  
         Le <xref:System.Threading.AsyncLocal%601?displayProperty=fullName> classe permet de représenter des données ambiantes qui sont locales à un flux de contrôle asynchrone donné, tel qu’une `async` (méthode). Elle peut être utilisée pour conserver les données entre plusieurs threads. Vous pouvez également définir une méthode de rappel qui est avertie chaque fois que les données ambiantes changent, soit parce que le <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=fullName> propriété a été modifiée explicitement, soit parce que le thread a rencontré une transition de contexte.  
  
         Trois méthodes pratiques, <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=fullName>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=fullName>, et <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=fullName>, ont été ajoutées à la base de tâches asynchrones (TAP) pour renvoyer les tâches terminées dans un état particulier.  
  
         Le <xref:System.IO.Pipes.NamedPipeClientStream> classe prend désormais en charge la communication asynchrone avec ses nouveaux <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>. .  
  
    -   **EventSource prend désormais en charge l’écriture dans le journal des événements**  
  
         Vous pouvez maintenant utiliser le <xref:System.Diagnostics.Tracing.EventSource> classe journal administratif ou opérationnel des messages dans le journal des événements, en outre à des sessions ETW existantes créées sur l’ordinateur. Par le passé, vous deviez utiliser le package Microsoft.Diagnostics.Tracing.EventSource NuGet pour cette fonctionnalité. Cette fonctionnalité est désormais intégrée au .NET Framework 4.6.  
  
         Le package NuGet et le 4.6 Framework .NET ont tous deux été mis à jour avec les fonctionnalités suivantes :  
  
        -   **Événements dynamiques**  
  
             Permet que les événements soient définis « à la volée », sans créer de méthodes d'événement.  
  
        -   **Charges utiles de riches**  
  
             Permet que les tableaux et les classes avec attributs spécifiques, ainsi que les types primitifs, soient transmis comme charge utile  
  
        -   **Suivi de l’activité**  
  
             Tous les événements entre les événements de début et de fin sont marqués avec un ID qui représente toutes les activités en cours.  
  
         Pour prendre en charge ces fonctionnalités, surchargées <xref:System.Diagnostics.Tracing.EventSource.Write%2A> méthode a été ajoutée à la <xref:System.Diagnostics.Tracing.EventSource> classe.  
  
-   **Windows Presentation Foundation (WPF)**  
  
    -   **Améliorations de HDPI**  
  
         La prise en charge HDPI dans WPF est désormais mieux assurée dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Des améliorations ont été apportées à l'arrondi de disposition pour réduire les instances de découpage dans les contrôles avec bordures. Par défaut, cette fonctionnalité est activée uniquement si votre <xref:System.Runtime.Versioning.TargetFrameworkAttribute> est définie sur .NET 4.6.  Les applications qui ciblent des versions antérieures du framework mais sont exécutent le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] pouvez participer au nouveau comportement en ajoutant la ligne suivante à la [ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section du fichier app.config :  
  
        ```  
  
        <AppContextSwitchOverrides  
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"  
        />  
  
        ```  
  
         Les fenêtres WPF chevauchant plusieurs écrans avec différents paramètres DPI (programme d'installation multi-DPI) sont à présent restituées entièrement sans zones obscurcies. Vous pouvez désactiver ce comportement en ajoutant la ligne suivante à la section `<appSettings>` du fichier app.config :  
  
        ```  
  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
  
        ```  
  
         Prise en charge de charger automatiquement le curseur vers la droite selon le paramètre PPP a été ajouté à <xref:System.Windows.Input.Cursor?displayProperty=fullName>.  
  
    -   **Touch est meilleure**  
  
         Client de rapports sur [connexion](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) qui touch produit un comportement imprévisible ont été traités dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Le seuil de double appui pour les applications du Windows Store et les applications WPF est maintenant le même que dans Windows 8.1 et versions ultérieures.  
  
    -   **Prise en charge de la fenêtre enfant transparent**  
  
         WPF dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] prend en charge les fenêtres enfants transparentes dans Windows 8.1 et versions ultérieures. Cela vous permet de créer des fenêtres enfants non rectangulaires et transparentes dans vos fenêtres de niveau supérieur. Vous pouvez activer cette fonctionnalité en définissant le <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=fullName> propriété `true`.  
  
-   **Windows Communication Foundation (WCF)**  
  
    -   **Prise en charge SSL**  
  
         WCF prend désormais en charge la version TLS 1.1 et TLS 1.2 de SSL, en plus de SSL 3.0 et TLS 1.0, lorsque vous utilisez NetTcp avec l'authentification client et la sécurité de transport. Il est désormais possible de sélectionner le protocole à utiliser, ou de désactiver les anciens protocoles moins sécurisés. Cette opération peut être effectuée en définissant le <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> propriété ou en ajoutant le code suivant dans un fichier de configuration.  
  
        ```  
        <netTcpBinding>  
           <binding>  
              <security mode= "None|Transport|Message|TransportWithMessageCredential" >  
                 <transport clientCredentialType="None|Windows|Certificate"  
                            protectionLevel="None|Sign|EncryptAndSign"  
                            sslProtocols="Ssl3|Tls1|Tls11|Tls12">  
                    </transport>  
              </security>  
           </binding>  
        </netTcpBinding>  
  
        ```  
  
    -   **Envoi de messages à l’aide de différentes connexions HTTP**  
  
         WCF permet désormais aux utilisateurs de s'assurer que certains messages sont envoyés à l'aide de différentes connexions HTTP sous-jacentes. Il existe deux façons d'effectuer cette opération :  
  
        -   **À l’aide d’un préfixe de nom de groupe de connexion**  
  
             Les utilisateurs peuvent spécifier une chaîne que WCF utilisera comme préfixe du nom de groupe de connexion. Deux messages avec des préfixes différents sont envoyés à l'aide de différentes connexions HTTP sous-jacentes. Vous définissez le préfixe en ajoutant une paire clé/valeur à du message <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=fullName> propriété. La clé est « HttpTransportConnectionGroupNamePrefix » ; la valeur est le préfixe de votre choix.  
  
        -   **À l’aide de différentes fabriques de canaux**  
  
             Les utilisateurs peuvent aussi activer une fonctionnalité qui permet de s'assurer que les messages envoyés à l'aide de canaux créés par différentes fabriques de canaux utilisent différentes connexions HTTP sous-jacentes. Pour activer cette fonctionnalité, les utilisateurs doivent définir la propriété `appSetting` suivante avec la valeur `true` :  
  
            ```  
  
            <appSettings>  
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />  
            </appSettings>  
  
            ```  
  
-   **Windows Workflow Foundation (WWF)**  
  
     Vous pouvez maintenant spécifier le nombre de secondes pendant lesquelles un service de workflow maintient une demande d'opération exceptionnelle quand il existe un signet « non-protocole » en attente avant l'expiration de la demande. Un signet « non-protocole » est un signet qui n'est pas lié à des activités de réception en attente. Comme certaines activités créent des signets non-protocole dans leur implémentation, il peut ne pas être évident qu'un signet non-protocole existe. Ceux-ci incluent État et Prélèvement. Par conséquent, si vous avez un service de workflow mis en œuvre avec une machine à états ou contenant une activité de prélèvement, vous aurez probablement des signets non-protocole. Vous spécifiez l'intervalle en ajoutant la ligne suivante à la section `appSettings` de votre fichier app.config :  
  
    ```  
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>  
    ```  
  
     La valeur par défaut est 60 secondes. Si `value` a la valeur 0, les demandes exceptionnelles sont immédiatement rejetées comme erreur avec un texte tel que le suivant :  
  
    ```Output  
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.   
    ```  
  
     C'est le même message que vous recevez en cas d'opération exceptionnelle et d'absence de signet non-protocole.  
  
     Si la valeur de l'élément `FilterResumeTimeoutInSeconds` est différente de zéro, il existe des signets non-protocole, l'intervalle de délai d'attente expire et l'opération échoue avec un message d'expiration.  
  
-   **Transactions**  
  
     Vous pouvez désormais inclure l’identificateur de transaction distribuée pour la transaction qui a provoqué une exception dérivée de <xref:System.Transactions.TransactionException> levée. Pour ce faire, ajoutez la clé suivante à la section `appSettings` de votre fichier app.config :  
  
    ```  
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>   
    ```  
  
     La valeur par défaut est `false`.  
  
-   **Mise en réseau**  
  
    -   **Réutilisation de socket**  
  
         Windows 10 inclut un nouvel algorithme de mise en réseau à haute scalabilité qui améliore l'utilisation des ressources de l'ordinateur en réutilisant les ports locaux pour les connexions TCP sortantes. Le .NET Framework 4.6 prend en charge le nouvel algorithme, permettant aux applications .NET de tirer parti du nouveau comportement. Dans les précédentes versions de Windows, il y avait une limite artificielle de connexions simultanées (généralement 16 384, taille par défaut de la plage de ports dynamiques), ce qui pouvait limiter la scalabilité d'un service en provoquant l'épuisement du port sous charge.  
  
         Dans le [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], deux nouvelles API ont été ajoutées pour permettre la réutilisation de port, ce qui supprime la limite de 64 Ko sur les connexions simultanées :  
  
        -   Le <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName> valeur d’énumération.  
  
        -   Le <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName> propriété.  
  
         Par défaut, le <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName> propriété `false` , sauf si la `HWRPortReuseOnSocketBind` valeur de la `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` clé de Registre est définie sur 0 x 1. Pour activer la réutilisation de port local sur les connexions HTTP, définissez la <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName> propriété `true`. Cela entraîne de toutes les connexions de socket TCP sortantes à partir de <xref:System.Net.Http.HttpClient> et <xref:System.Net.HttpWebRequest> à utiliser une nouvelle option de socket Windows 10, [SO_REUSE_UNICASTPORT](https://msdn.microsoft.com/library/windows/desktop/ms740532.aspx), qui permet la réutilisation de port local.  
  
         Les développeurs écrivant une application de sockets peuvent spécifier le <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName> option lorsque vous appelez une méthode comme <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=fullName> afin que les sockets sortants réutiliser des ports locaux lors de la liaison.  
  
    -   **Prise en charge des noms de domaine internationaux et PunyCode**  
  
         Une nouvelle propriété, <xref:System.Uri.IdnHost%2A>, a été ajouté à la <xref:System.Uri> classe pour mieux prendre en charge des noms de domaine internationaux et PunyCode.  
  
-   **Redimensionnement dans les contrôles Windows Forms.**  
  
     Cette fonctionnalité a été développée dans [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] pour inclure le <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> et <xref:System.Windows.Forms.ToolStripSplitButton> types et le rectangle spécifié par le <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> propriété utilisée lors du dessin un <xref:System.Drawing.Design.UITypeEditor>.  
  
     Il est nécessaire d'accepter cette fonctionnalité. Pour l'activer, affectez à l'élément `EnableWindowsFormsHighDpiAutoResizing` la valeur `true` dans le fichier de configuration de l'application (app.config) :  
  
    ```  
  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
  
    ```  
  
-   **Prise en charge des codages de page de codes**  
  
     [!INCLUDE[net_core](../../../includes/net-core-md.md)] prend en charge principalement les codages Unicode, et fournit par défaut une prise en charge limitée des codages de pages de codes. Vous pouvez ajouter la prise en charge des codages de page de codes disponibles dans le .NET Framework mais non pris en charge dans [!INCLUDE[net_core](../../../includes/net-core-md.md)] en inscrivant les codages de page de code avec la <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=fullName> (méthode). Pour plus d’informations, consultez [System.Text.CodePagesEncodingProvider](https://msdn.microsoft.com/en-us/library/system.text.codepagesencodingprovider.aspx).  
  
-   **.NET native**  
  
     Les applications Windows pour Windows 10 qui ciblent le [!INCLUDE[net_core](../../../includes/net-core-md.md)] et sont écrites en C# ou Visual Basic peuvent désormais tirer parti d'une nouvelle technologie qui compile les applications en code natif plutôt qu'en code IL (Intermediate Language). Il en résulte des applications caractérisées par un démarrage plus rapide et un temps d'exécution accéléré. Pour plus d’informations, consultez [compilation d’applications avec .NET Native](../../../docs/framework/net-native/index.md). Pour une vue d’ensemble de .NET Native illustrant comment il diffère de la compilation JIT et NGEN et ce que signifie pour votre code, consultez [.NET Native et Compilation](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
     Vos applications sont compilées en code natif par défaut dans Visual Studio 2015. Pour plus d’informations, consultez [mise en route avec .NET Native](../../../docs/framework/net-native/getting-started-with-net-native.md).  
  
     Pour permettre la prise en charge du débogage des applications .NET Native, un certain nombre de nouvelles interfaces et d'énumérations ont été ajoutées à l'API de débogage non managée. Pour plus d’informations, consultez la [débogage (référence des API non managées)](../../../ml/index.xml) rubrique.  
  
-   **Packages Open source .NET Framework**  
  
     [!INCLUDE[net_core](../../../includes/net-core-md.md)]packages, tels que les collections immuables, [API SIMD](http://go.microsoft.com/fwlink/?LinkID=518639), et les API de réseau tels que ceux trouvés dans le <xref:System.Net.Http> espace de noms sont désormais disponibles en tant que packages open source sur [GitHub](https://github.com/). Pour accéder au code, consultez [NetFx sur GitHub](http://go.microsoft.com/fwlink/?LinkID=518634). Pour plus d’informations et contribuer à ces packages, consultez [.NET Core et Open Source](../../../docs/framework/get-started/net-core-and-open-source.md), [Page d’accueil .NET sur GitHub](http://go.microsoft.com/fwlink/?LinkID=518635).  
  
 [Retour au début](#introduction)  
  
<a name="v452"></a>   
## <a name="whats-new-in-the-net-framework-452"></a>Nouveautés dans le .NET Framework 4.5.2  
  
-   **Nouvelles API pour les applications ASP.NET.** La nouvelle <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=fullName> et <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=fullName> méthodes vous permettent d’inspecter et modifier les en-têtes de réponse et le code d’état que la réponse est vidée dans l’application cliente. Envisagez d’utiliser ces méthodes au lieu de la <xref:System.Web.HttpApplication.PreSendRequestHeaders> et <xref:System.Web.HttpApplication.PreSendRequestContent> événements ; ils sont plus efficaces et fiables.  
  
     Le <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=fullName> méthode vous permet de planifier des éléments de travail en arrière-plan petit. ASP.NET effectue le suivi de ces éléments et empêche IIS de mettre fin brutalement au processus de traitement tant que tous les éléments de travail en arrière-plan ne sont pas terminés. Cette méthode ne peut pas être appelée en dehors d'un domaine d'application managée ASP.NET.  
  
     La nouvelle <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=fullName> et <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=fullName> propriétés retournent des valeurs booléennes qui indiquent si les en-têtes de réponse ont été écrits. Vous pouvez utiliser ces propriétés pour vous assurer que les appels d’API tels que <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=fullName> (qui lèvent des exceptions si les en-têtes ont été écrits) réussit.  
  
-   **Redimensionnement dans les contrôles Windows Forms.** Cette fonctionnalité a été étendue. Vous pouvez maintenant utiliser le paramètre PPP système pour redimensionner les composants des contrôles supplémentaires suivants (par exemple, la flèche déroulante vers le bas dans les zones de liste modifiable) :  
  
     <xref:System.Windows.Forms.ComboBox>   
     <xref:System.Windows.Forms.ToolStripComboBox>   
     <xref:System.Windows.Forms.ToolStripMenuItem>   
     <xref:System.Windows.Forms.Cursor>   
     <xref:System.Windows.Forms.DataGridView>   
     <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
     Il est nécessaire d'accepter cette fonctionnalité. Pour l'activer, affectez à l'élément `EnableWindowsFormsHighDpiAutoResizing` la valeur `true` dans le fichier de configuration de l'application (app.config) :  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
-   **Nouvelle fonctionnalité de flux de travail.** Un gestionnaire de ressources qui utilise le <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> (méthode) (et par conséquent, l’implémentation la <xref:System.Transactions.IPromotableSinglePhaseNotification> interface) peut utiliser la nouvelle <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=fullName> méthode pour demander les éléments suivants :  
  
    -   la promotion de la transaction en transaction MSDTC (Microsoft Distributed Transaction Coordinator) ;  
  
    -   Remplacez <xref:System.Transactions.IPromotableSinglePhaseNotification> avec un <xref:System.Transactions.ISinglePhaseNotification>, qui est une inscription durable qui prend en charge les validations en une seule phase.  
  
     Ces demandes peuvent être faites au sein du même domaine d'application et ne nécessitent pas de code non managé supplémentaire pour interagir avec MSDTC pour effectuer la promotion. La nouvelle méthode peut être appelée uniquement s’il existe un appel en attente à partir de <xref:System.Transactions?displayProperty=fullName> à la <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` méthode implémentée par l’inscription peut être promue.  
  
-   **Améliorations du profilage.** Les nouvelles API de profilage non managées suivantes proposent un profilage plus robuste :  
  
     [Cor_prf_assembly_reference_info, Structure](../../../ocs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)   
     [COR_PRF_MODULE_FLAGS, énumération](../../../ocs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)   
     [Getassemblyreferences, méthode](../Topic/ICorProfilerCallback6::GetAssemblyReferences%20Method.md)   
     [Geteventmask2, méthode](../Topic/ICorProfilerInfo5::GetEventMask2%20Method.md)   
     [Seteventmask2, méthode](../Topic/ICorProfilerInfo5::SetEventMask2%20Method.md)   
     [AddAssemblyReference, méthode](../Topic/ICorProfilerAssemblyReferenceProvider::AddAssemblyReference%20Method.md)  
  
     Les implémentations précédentes d'`ICorProfiler` prenaient en charge le chargement tardif des assemblys dépendants. Les nouvelles API de profilage ont besoin que les assemblys dépendants soient injectés par le profileur pour qu'ils puissent être chargés immédiatement, plutôt qu'une fois que l'application est entièrement initialisée. Cette modification ne concerne pas les utilisateurs des API `ICorProfiler` existantes.  
  
-   **Améliorations du débogage.** Les nouvelles API de débogage non managées suivantes améliorent l'intégration à un profileur. Vous pouvez à présent accéder aux métadonnées insérées par le profileur ainsi qu'aux variables locales et au code produit par les demandes ReJIT du compilateur pendant le débogage de dump.  
  
     [Setwriteablemetadataupdatemode, méthode](../Topic/ICorDebugProcess7::SetWriteableMetadataUpdateMode%20Method.md)   
     [Enumeratelocalvariablesex, méthode](../Topic/ICorDebugILFrame4::EnumerateLocalVariablesEx%20Method.md)   
     [Getlocalvariableex, méthode](../Topic/ICorDebugILFrame4::GetLocalVariableEx%20Method.md)   
     [Getcodeex, méthode](../Topic/ICorDebugILFrame4::GetCodeEx%20Method.md)   
     [Getactiverejitrequestilcode, méthode](../Topic/ICorDebugFunction3::GetActiveReJitRequestILCode%20Method.md)   
     [Getinstrumentedilmap, méthode](../Topic/ICorDebugILCode2::GetInstrumentedILMap%20Method.md)  
  
-   **Modifications de suivi d’événements.** .NET Framework 4.5.2 permet le traçage des activités de type Suivi d'événements pour Windows (ETW) hors processus pour une surface d'exposition plus importante. Ce dernier permet aux fournisseurs de gestion avancée de l'alimentation (APM) de fournir des outils légers qui suivent avec précision les coûts des demandes et activités individuelles qui traversent les threads.  Ces événements sont déclenchés uniquement quand les contrôleurs ETW les autorisent ; par conséquent, les modifications ne concernent pas le code ETW écrit auparavant ni le code qui s'exécute avec la fonctionnalité ETW désactivée.  
  
-   **La promotion d’une transaction et en le convertissant en une inscription durable**  
  
     <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=fullName> est une nouvelle API ajoutée au .NET Framework 4.5.2 et 4.6 :  
  
    ```  
  
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,  
                                              IPromotableSinglePhaseNotification promotableNotification,  
                                              ISinglePhaseNotification enlistmentNotification,  
                                              EnlistmentOptions enlistmentOptions)  
  
    ```  
  
     La méthode peut être utilisée par une inscription qui a été créée précédemment par <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=fullName> en réponse à la <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=fullName> (méthode). Elle demande à `System.Transactions` de promouvoir la transaction en une transaction MSDTC et de « convertir » l'inscription à promouvoir en une inscription durable. Une fois que cette méthode se termine correctement, la <xref:System.Transactions.IPromotableSinglePhaseNotification> interface sera n’est plus référencée par `System.Transactions`, et toutes les futures notifications arrivent sur les <xref:System.Transactions.ISinglePhaseNotification> interface. L'inscription en question doit agir comme inscription durable, en prenant en charge la récupération et la journalisation des transactions. Reportez-vous à <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=fullName> pour plus d’informations. En outre, l’inscription doit prendre en charge <xref:System.Transactions.ISinglePhaseNotification>.  Cette méthode peut *uniquement* être appelée lors du traitement un <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=fullName> appeler. Si vous n’est pas le cas, un <xref:System.Transactions.TransactionException> exception est levée.  
  
 [Retour au début](#introduction)  
  
<a name="v451"></a>   
## <a name="whats-new-in-the-net-framework-451"></a>Nouveautés dans le .NET Framework 4.5.1  
 **Mises à jour avril 2014**:  
  
-   [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658) inclut les mises à jour des modèles de la bibliothèque de classes Portable pour prendre en charge ces scénarios :  
  
    -   Vous pouvez utiliser les API Windows Runtime dans les bibliothèques portables qui ciblent Windows 8.1, Windows Phone 8.1, et Windows Phone Silverlight 8.1.  
  
    -   Vous pouvez inclure du code XAML (type Windows.UI.XAML) dans les bibliothèques portables quand vous ciblez Windows 8.1 ou Windows Phone 8.1. Les modèles XAML suivants sont pris en charge : Page vierge, Dictionnaire de ressources, Contrôle basé sur un modèle et Contrôle utilisateur.  
  
    -   Vous pouvez créer un composant Windows Runtime portable (fichier .winmd) à utiliser dans les applications du Windows Store qui ciblent Windows 8.1 et Windows Phone 8.1.  
  
    -   Vous pouvez recibler une bibliothèque de classes du Windows Store ou du Windows Phone Store, par exemple une bibliothèque de classes portable.  
  
     Pour plus d’informations sur ces modifications, consultez [bibliothèque de classes Portable](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).  
  
-   Le jeu de contenus du .NET Framework inclut à présent la documentation relative à [!INCLUDE[net_native](../../../includes/net-native-md.md)], une technologie de précompilation qui permet de générer et déployer des applications Windows. [!INCLUDE[net_native](../../../includes/net-native-md.md)] compile directement vos applications en code natif, plutôt qu'en langage intermédiaire, pour de meilleures performances. Pour plus d’informations, consultez [compilation d’applications avec .NET Native](../../../docs/framework/net-native/index.md).  
  
-   Le [.NET Framework Reference Source](http://referencesource.microsoft.com/) offre une nouvelle expérience de navigation et des fonctionnalités améliorées. Vous pouvez maintenant parcourir le code de source de .NET Framework en ligne, [télécharger la référence](http://referencesource.microsoft.com/download.html) pour consultation hors connexion et parcourir les sources (y compris les correctifs et mises à jour) pendant le débogage. Pour plus d’informations, consultez le billet de blog [un nouveau look pour .NET Reference Source](http://blogs.msdn.com/b/dotnet/archive/2014/02/24/a-new-look-for-net-reference-source.aspx).  
  
 Les principales fonctionnalités et améliorations nouvelles dans le .NET Framework 4.5.1 sont les suivantes :  
  
-   Redirection de liaison automatique des assemblys. Depuis [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], lorsque vous compilez une application qui cible [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], il est possible d'ajouter des redirections de liaison au fichier de configuration de l'application, si votre application ou ses composants référencent plusieurs versions du même assembly. Vous pouvez également activer cette fonctionnalité pour les projets qui ciblent des versions antérieures du .NET Framework. Pour plus d’informations, consultez [Comment : activer et désactiver la Redirection de liaison automatique](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).  
  
-   Capacité à collecter des informations de diagnostic pour aider les développeurs à améliorer les performances des applications serveur et cloud. Pour plus d’informations, consultez la <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> et <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> méthodes dans le <xref:System.Diagnostics.Tracing.EventSource> classe.  
  
-   Capacité à compacter explicitement le tas d'objets volumineux (LOH) pendant un garbage collection. Pour plus d’informations, consultez la <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName> propriété.  
  
-   Autres améliorations des performances, telles que la suspension d'application ASP.NET, les améliorations JIT multicœurs et le démarrage accéléré des applications après une mise à jour du .NET Framework. Pour plus d’informations, consultez la [annonce de .NET Framework 4.5.1](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx) et [ASP.NET app suspend](http://blogs.msdn.com/b/dotnet/archive/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting.aspx) billet de blog.  
  
 Les améliorations apportées à Windows Forms incluent :  
  
-   Redimensionnement dans les contrôles Windows Forms. Vous pouvez utiliser le paramètre PPP système pour redimensionner les composants des contrôles (par exemple, les icônes qui apparaissent dans une grille des propriétés) en choisissant de l'utiliser pour votre application grâce à une entrée dans le fichier de configuration de l'application (app.config). Cette fonctionnalité est actuellement prise en charge dans les contrôles Windows Forms suivants :  
  
     <xref:System.Windows.Forms.PropertyGrid>   
     <xref:System.Windows.Forms.TreeView>   
     Certains aspects de la <xref:System.Windows.Forms.DataGridView> (voir [nouvelles fonctionnalités dans 4.5.2](#v452) de contrôles supplémentaires pris en charge)  
  
     Pour activer cette fonctionnalité, ajoutez un nouveau <> \> élément au fichier de configuration (app.config) et affectez le `EnableWindowsFormsHighDpiAutoResizing` élément `true`:  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
 Les améliorations lors du débogage de vos applications .NET Framework dans [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] incluent :  
  
-   Valeurs de retour dans le débogueur Visual Studio. Lorsque vous déboguez une application managée dans [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], la Fenêtre Automatique affiche les types et les valeurs de retour pour les méthodes. Ces informations sont disponibles pour les applications de bureau, Windows Store et Windows Phone. Pour plus d’informations, consultez [Examine les valeurs de retour d’appels de méthode](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f\(v=vs.120\).aspx) dans MSDN Library.  
  
-   Modifier & Continuer pour applications 64 bits. [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] prend en charge la fonctionnalité Modifier & Continuer pour les applications managées 64 bits pour le Bureau, Windows Store et Windows Phone. Les limitations existantes restent en vigueur pour les applications 32 bits et 64 bits (consultez la dernière section de la [les modifications de Code prises en charge (c#)](http://msdn.microsoft.com/library/ms164927\(v=vs.120\).aspx) article).  
  
-   Débogage asynchrone. Pour simplifier le débogage des applications asynchrones dans [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], la pile d'appels masque le code d'infrastructure fourni par les compilateurs pour prendre en charge la programmation asynchrone. Elle chaîne également les trames parentes logiques afin que vous puissiez suivre plus clairement l'exécution logique du programme. Une fenêtre Tâches remplace la fenêtre Tâches parallèles et affiche les tâches relatives à un point d'arrêt particulier, ainsi que toutes les autres tâches qui sont actuellement actives ou planifiées dans l'application. Vous pouvez consulter cette fonctionnalité dans la section « débogage asynchrone » de la [annonce de .NET Framework 4.5.1](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx).  
  
-   Meilleure prise en charge des exceptions pour les composants Windows Runtime. Dans [!INCLUDE[win81](../../../includes/win81-md.md)], une exception qui provient des applications Windows Store conserve les informations sur l'erreur qui a provoqué l'exception, même au-delà des limites du langage. Vous pouvez consulter cette fonctionnalité dans la section « Développement d’applications du Windows Store » de la [annonce de .NET Framework 4.5.1](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx).  
  
 Commençant par [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], vous pouvez utiliser la [profil guidée outil d’optimisation managé (Mpgo.exe)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md) pour optimiser [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] applications ainsi que les applications de bureau.  
  
 Pour les nouvelles fonctionnalités dans ASP.NET 4.5.1,, consultez [ASP.NET 4.5.1 et Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) sur le site ASP.NET.  
  
 [Retour au début](#introduction)  
  
<a name="core"></a>   
## <a name="whats-new-in-the-net-framework-45"></a>Nouveautés dans le .NET Framework 4.5  
  
### <a name="core-new-features-and-improvements"></a>Principales fonctionnalités et améliorations nouvelles  
  
-   Capacité à réduire les redémarrages du système en détectant et en fermant les applications .NET Framework 4 pendant le déploiement. Consultez la page [réduction des redémarrages système lors des Installations de .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md).  
  
-   Prise en charge de tableaux supérieurs à 2 gigaoctets (Go) sur les plateformes 64 bits. Cette fonctionnalité peut être activée dans le fichier de configuration de l'application. Consultez le [ <> \> élément](../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), qui répertorie également d’autres restrictions sur la taille de l’objet et la taille du tableau.  
  
-   Meilleures performances via une opération garbage collection en arrière-plan pour les serveurs. Lorsque vous utilisez le garbage collection de serveur dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], le garbage collection en arrière-plan est automatiquement activé. Consultez la section Garbage Collection côté serveur en arrière-plan de la [principes de base du Garbage Collection](../../../docs/standard/garbage-collection/fundamentals.md) rubrique.  
  
-   Compilation juste-à-temps (JIT) en arrière-plan, disponible en option sur les processeurs multicœurs pour améliorer les performances de l'application. Consultez la page <xref:System.Runtime.ProfileOptimization>.  
  
-   Capacité à limiter la durée pendant laquelle le moteur d'expressions régulières tentera de résoudre une expression régulière avant d'expirer. Consultez le <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=fullName> propriété.  
  
-   Capacité à définir la culture par défaut d'un domaine d'application. Consultez le <xref:System.Globalization.CultureInfo> classe.  
  
-   Prise en charge de la console pour l'encodage Unicode (UTF-16). Consultez le <xref:System.Console> classe.  
  
-   Prise en charge du versioning des données de classement et de comparaison des chaînes culturelles. Consultez le <xref:System.Globalization.SortVersion> (classe).  
  
-   Meilleures performances lors de l'extraction des ressources. Consultez la page [empaquetage et déploiement de ressources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
-   Améliorations de la compression Zip pour réduire la taille d'un fichier compressé. Consultez le <xref:System.IO.Compression?displayProperty=fullName> espace de noms.  
  
-   Possibilité de personnaliser un contexte de réflexion pour remplacer le comportement de réflexion par défaut via la <xref:System.Reflection.Context.CustomReflectionContext> (classe).  
  
-   Prise en charge de la version 2008 des noms de domaine internationaux dans les Applications IDNA () standard quand le <xref:System.Globalization.IdnMapping?displayProperty=fullName> classe est utilisée sur [!INCLUDE[win8](../../../includes/win8-md.md)].  
  
-   Délégation de comparaison de chaînes au système d'exploitation, qui implémente Unicode 6.0, lorsque .NET Framework est utilisé dans [!INCLUDE[win8](../../../includes/win8-md.md)]. Lorsqu'il s'exécute sur d'autres plateformes, .NET Framework inclut ses propres données de comparaison de chaînes, qui implémentent Unicode 5.x. Consultez le <xref:System.String> (classe) et la section Notes de la <xref:System.Globalization.SortVersion> (classe).  
  
-   Possibilité de calculer les codes de hachage des chaînes par domaine d'application. See [<>\> Element](../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).  
  
-   Prise en charge de la réflexion fractionnée entre type <xref:System.Type> et <xref:System.Reflection.TypeInfo> classes. Consultez la page [réflexion dans le .NET Framework pour les applications du Windows Store](../../../docs/framework/reflection-and-codedom/reflection-for-windows-store-apps.md).  
  
### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)  
 Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], le package Managed Extensibility Framework (MEF) fournit les nouvelles fonctionnalités suivantes :  
  
-   Prise en charge des types génériques.  
  
-   Modèle de programmation basé sur les conventions qui permet de créer des parties basées sur les conventions d'appellation, plutôt que sur les attributs.  
  
-   Portées multiples.  
  
-   Sous-ensemble MEF que vous pouvez utiliser lorsque vous créez des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Ce sous-ensemble est disponible comme un [package téléchargeable](http://go.microsoft.com/fwlink/?LinkId=256238) à partir de la galerie NuGet. Pour installer le package, ouvrez votre projet dans Visual Studio, choisissez **Manage NuGet Packages** à partir de la **projet** menu, puis recherchez en ligne pour le `Microsoft.Composition` package.  
  
 Pour plus d’informations, consultez [Managed Extensibility Framework (MEF)](../../../docs/framework/mef/index.md).  
  
### <a name="asynchronous-file-operations"></a>Opérations asynchrones sur les fichiers  
 Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], de nouvelles fonctionnalités asynchrones ont été ajoutées aux langages C# et Visual Basic. Ces fonctionnalités ajoutent un modèle basé sur les tâches pour exécuter des opérations asynchrones. Pour utiliser ce nouveau modèle, utilisez les méthodes asynchrones dans les classes d'E/S. Consultez la page [d’e/s de fichier asynchrone](../../../docs/standard/io/e-s-sur-fichier-asynchrones.md).  
  
<a name="tools"></a>   
### <a name="tools"></a>Outils  
 Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], l'outil Resource File Generator (Resgen.exe) vous permet de créer un fichier .resw à utiliser dans les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] à partir d'un fichier .resources incorporé dans un assembly .NET Framework. Pour plus d’informations, consultez [Resgen.exe (Resource File Generator)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).  
  
 L'outil d'optimisation guidée par profil managé (Mpgo.exe) vous permet d'améliorer le temps de démarrage de l'application, l'utilisation de la mémoire (taille du jeu de travail) et le débit en optimisant les assemblys d'image natifs. L'outil en ligne de commande génère des données de profil pour les assemblys natifs d'application graphique. Consultez la page [Mpgo.exe (outil d’optimisation guidée par profil managé)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md). Depuis [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], vous pouvez utiliser Mpgo.exe pour optimiser les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], ainsi que les applications de bureau.  
  
<a name="parallel"></a>   
### <a name="parallel-computing"></a>Calcul parallèle  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] fournit plusieurs nouvelles fonctionnalités et améliorations pour le calcul parallèle. Il s'agit notamment de performances améliorées, d'un contrôle accru, d'une prise en charge améliorée pour la programmation asynchrone, d'une nouvelle bibliothèque de flux de données et d'une prise en charge améliorée pour le débogage parallèle et l'analyse des performances. Consultez l’entrée [What ' s New for Parallelism dans .NET 4.5](http://go.microsoft.com/fwlink/?LinkId=235061) dans le blog programmation parallèle avec .NET.  
  
<a name="web"></a>   
### <a name="web"></a>Web  
 ASP.NET 4.5 et 4.5.1 ajoutent la liaison de modèle pour Web Forms, la prise en charge de WebSocket, les gestionnaires asynchrones, les améliorations de performances et de nombreuses autres fonctionnalités. Pour plus d'informations, reportez-vous aux ressources suivantes :  
  
-   [ASP.NET 4.5 et Visual Studio 2012](../Topic/ASP.NET%20Core%20and%20Visual%20Studio%202015.md) dans MSDN Library.  
  
-   [ASP.NET 4.5.1 et Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) sur le site ASP.NET.  
  
<a name="networking"></a>   
### <a name="networking"></a>Mise en réseau  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] fournit une nouvelle interface de programmation pour les applications HTTP. Pour plus d’informations, consultez les nouveaux <xref:System.Net.Http?displayProperty=fullName> et <xref:System.Net.Http.Headers?displayProperty=fullName> espaces de noms.  
  
 Prise en charge est également inclus pour une nouvelle interface de programmation pour accepter et d’interagir avec une connexion WebSocket à l’aide d’existant <xref:System.Net.HttpListener> et les classes connexes. Pour plus d’informations, consultez les nouveaux <xref:System.Net.WebSockets> espace de noms et le <xref:System.Net.HttpListener> classe.  
  
 En outre, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] inclut les améliorations de mise en réseau suivantes :  
  
-   Prise en charge URI conforme aux documents RFC. Pour plus d’informations, consultez <xref:System.Uri> et les classes connexes.  
  
-   Prise en charge des analyses du nom de domaine international (IDN, Internationalized Domain Name). Pour plus d’informations, consultez <xref:System.Uri> et les classes connexes.  
  
-   Prise en charge de l'internationalisation des adresses de messagerie. Pour plus d’informations, consultez la <xref:System.Net.Mail> espace de noms.  
  
-   Prise en charge d'IPv6 améliorée. Pour plus d’informations, consultez la <xref:System.Net.NetworkInformation> espace de noms.  
  
-   Prise en charge du socket en mode double. Pour plus d’informations, consultez la <xref:System.Net.Sockets.Socket> et <xref:System.Net.Sockets.TcpListener> classes.  
  
<a name="client"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Windows Presentation Foundation (WPF) présente des modifications et des améliorations dans les domaines suivants :  
  
-   La nouvelle <xref:System.Windows.Controls.Ribbon.Ribbon> contrôle, ce qui vous permet d’implémenter une interface utilisateur du ruban qui héberge une barre d’outils Accès rapide, Menu de l’Application et des onglets.  
  
-   La nouvelle <xref:System.ComponentModel.INotifyDataErrorInfo> interface, qui prend en charge la validation de données synchrones et asynchrones.  
  
-   Nouvelles fonctionnalités pour le <xref:System.Windows.Controls.VirtualizingPanel> et <xref:System.Windows.Threading.Dispatcher> classes.  
  
-   Performances améliorées lors de l'affichage de grands ensembles de données groupées et lors de l'accès aux collections sur les threads autres que ceux d'interface utilisateur.  
  
-   Liaison de données pour les propriétés statiques, liaison de données personnalisée types qui implémentent la <xref:System.Reflection.ICustomTypeProvider> interface et la récupération d’informations de liaison de données à partir d’une expression de liaison.  
  
-   Repositionnement des données au fur et à mesure du changement des valeurs (mise en forme active).  
  
-   Possibilité de vérifier si le contexte de données d'un conteneur d'éléments est déconnecté.  
  
-   Possibilité de définir la durée qui doit s'écouler entre les modifications de propriété et les mises à jour de la source de données.  
  
-   Prise en charge améliorée pour implémenter des modèles d'événement faible. De plus, les événements peuvent maintenant accepter des extensions de balisage.  
  
<a name="windows_communication_foundation"></a>   
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
 Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les fonctionnalités suivantes ont été ajoutées pour faciliter l'écriture et l'entretien des applications Windows Communication Foundation (WCF) :  
  
-   Simplification des fichiers de configuration générés.  
  
-   Prise en charge du développement Contrat en premier.  
  
-   Possibilité de configurer plus facilement le mode de compatibilité ASP.NET.  
  
-   Modifications des valeurs de propriété de transport par défaut pour réduire la probabilité d'avoir à les définir.  
  
-   Met à jour la <xref:System.Xml.XmlDictionaryReaderQuotas> classe afin de réduire la probabilité que vous devrez configurer manuellement les quotas pour les lecteurs de dictionnaire XML.  
  
-   Validation des fichiers de configuration WCF par Visual Studio dans le cadre du processus de génération, afin que vous puissiez détecter les erreurs de configuration avant d'exécuter votre application.  
  
-   Nouvelle prise en charge de la diffusion en continu asynchrone.  
  
-   Nouveau mappage de protocole HTTPS pour simplifier l'exposition d'un point de terminaison via HTTPS à l'aide des services Internet (IIS).  
  
-   Possibilité de générer des métadonnées dans un document WSDL unique en ajoutant `?singleWSDL` à l'URL de service.  
  
-   Prise en charge Websockets pour activer une véritable communication bidirectionnelle sur les ports 80 et 443 avec des caractéristiques de performances semblables à celles du transport TCP.  
  
-   Prise en charge de la configuration des services dans le code.  
  
-   Info-bulles de l'éditeur XML.  
  
-   <xref:System.ServiceModel.ChannelFactory> prise en charge de la mise en cache.  
  
-   Prise en charge de la compression d'encodage binaire.  
  
-   Prise en charge d'un transport UDP qui permet aux développeurs d'écrire des services qui utilisent une messagerie de type « Fire and Forget » (déclenché et oublié). Un client envoie un message à un service et n'attend aucune réponse de ce dernier.  
  
-   Possibilité de prendre en charge plusieurs modes d'authentification sur un point de terminaison WCF unique lors de l'utilisation du transport HTTP et de la sécurité du transport.  
  
-   Prise en charge des services WCF qui utilisent des noms IDN.  
  
 Pour plus d’informations, consultez [quelles sont les nouveautés dans Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=228173).  
  
<a name="windows_workflow_foundation"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 Dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], plusieurs nouvelles fonctionnalités ont été ajoutées à Windows Workflow Foundation (WF), notamment :  
  
-   État des workflows de machine, qui ont été introduites dans le cadre du .NET Framework 4.0.1 ([mise à jour 1 de la plateforme .NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=215092)). Cette mise à jour comprenait plusieurs classes et activités nouvelles qui permettaient aux développeurs de créer des flux de travail de machine à états. Ces classes et activités ont été mises à jour pour que [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] inclue les fonctionnalités suivantes :  
  
    -   Possibilité de définir des points d'arrêt sur les états.  
  
    -   Possibilité de copier et coller des transitions dans le concepteur de workflow.  
  
    -   Prise en charge du concepteur pour la création de transitions de déclencheur partagées.  
  
    -   Activités de création de workflows machine à états, notamment : <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, et <xref:System.Activities.Statements.Transition>.  
  
-   Fonctionnalités améliorées du Concepteur de flux de travail, dont notamment :  
  
    -   Davantage de possibilités de recherche de flux de travail dans Visual Studio, y compris **recherche rapide** et **rechercher dans les fichiers**.  
  
    -   Possibilité de créer automatiquement une activité de séquence lorsqu'une deuxième activité enfant est ajoutée à une activité de conteneur, et d'inclure les deux activités dans l'activité de séquence.  
  
    -   Prise en charge des panoramiques, ce qui permet à la partie visible d'un flux de travail d'être modifiée sans utiliser les barres de défilement.  
  
    -   Un nouveau **structure du Document** vue qui montre les composants d’un flux de travail dans une arborescence de style arborescent et vous permet de sélectionner un composant dans le **structure du Document** vue.  
  
    -   Possibilité d'ajouter des annotations aux activités.  
  
    -   Possibilité de définir et d'utiliser des délégués d'activité à l'aide du Concepteur de flux de travail.  
  
    -   Connexion automatique et insertion automatique des activités et des transitions dans les flux de travail de machine à états et d'organigramme.  
  
-   Stockage des informations d'état d'affichage pour un flux de travail dans un élément unique du fichier XAML, afin que vous puissiez facilement localiser et modifier les informations sur l'état d'affichage.  
  
-   Activité de conteneur NoPersistScope pour empêcher les activités enfants de devenir persistantes.  
  
-   Prise en charge des expressions C# :  
  
    -   Les projets de flux de travail qui utilisent Visual Basic utiliseront les expressions Visual Basic et les projets de flux de travail C# utiliseront les expressions C#.  
  
    -   Les projets de flux de travail C# qui ont été créés dans Visual Studio 2010 et qui possèdent des expressions Visual Basic sont compatibles avec les projets de flux de travail C# qui utilisent des expressions C#.  
  
-   Améliorations du contrôle de version :  
  
    -   La nouvelle <xref:System.Activities.WorkflowIdentity> (classe), qui fournit un mappage entre une instance de workflow persistante et sa définition de flux de travail.  
  
    -   L’exécution côte à côte de plusieurs versions de flux de travail dans le même hôte, y compris <xref:System.ServiceModel.Activities.WorkflowServiceHost>.  
  
    -   Dans une mise à jour dynamique, capacité à modifier la définition d'une instance de flux de travail rendue persistante.  
  
-   Développement de services de workflow « Contrat en premier », ce qui permet de générer automatiquement les activités correspondants à un contrat de service existant.  
  
 Pour plus d’informations, consultez [nouvelles fonctionnalités de Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=228176).  
  
<a name="tailored"></a>   
### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]  
 Les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] sont conçues pour des facteurs de forme spécifiques et tirent parti de la puissance du système d'exploitation Windows. Un sous-ensemble de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] ou 4.5.1 est disponible pour générer des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] pour Windows à l'aide de C# ou de Visual Basic. Ce sous-ensemble est appelé [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] et est décrit dans une [présentation](http://go.microsoft.com/fwlink/?LinkId=228491) dans le centre de développement Windows.  
  
<a name="portable"></a>   
### <a name="portable-class-libraries"></a>Bibliothèques de classes portables  
 Le projet Bibliothèque de classes portable dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] (et les versions ultérieures) vous permet d'écrire et de générer des assemblys managés qui fonctionnent sur plusieurs plateformes .NET Framework. Un projet Bibliothèque de classes portable vous permet de choisir les plateformes (telles que Windows Phone et [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]) à cibler. Les types et les membres disponibles dans votre projet sont automatiquement restreints aux types et aux membres communs entre ces plateformes. Pour plus d’informations, consultez [bibliothèque de classes Portable](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Le .NET Framework et les versions hors-bande](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)   
 [Quelles sont les nouveautés dans Visual Studio 2013](http://msdn.microsoft.com/library/bb386063\(v=vs.120\).aspx)   
 [ASP.NET 4.5.1 et Web Tools pour Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094)   
 [ASP.NET et Visual Studio pour le Web](../Topic/ASP.NET%20and%20Visual%20Studio%20for%20Web.md)   
 [Quelles sont les nouveautés dans Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=228173)   
 [Quelles sont les nouveautés dans Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkId=228176)   
 [Nouveautés de Visual C++](http://msdn.microsoft.com/library/hh409293\(v=vs.120\).aspx)