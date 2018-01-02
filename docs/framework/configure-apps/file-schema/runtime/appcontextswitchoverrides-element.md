---
title: "&lt;AppContextSwitchOverrides&gt; élément"
ms.custom: 
ms.date: 10/17/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AppContextSwitchOverrides
- compatibility switches
- configuration switches
- configuration
ms.assetid: 4ce07f47-7ddb-4d91-b067-501bd8b88752
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cc68f4be869a4773b8a6b932d1f6363855fe584
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ltappcontextswitchoverridesgt-element"></a>&lt;AppContextSwitchOverrides&gt; élément
Définit un ou plusieurs commutateurs utilisés par la classe <xref:System.AppContext> pour fournir un mécanisme d’annulation d’abonnement aux nouvelles fonctionnalités.  
  
 \<configuration>  
 \<runtime >  
\<AppContextSwitchOverrides >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<AppContextSwitchOverrides value="name1=value1[[;name2=value2];...]" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`value`|Attribut requis.<br /><br /> Définit un ou plusieurs noms de commutateur et leurs valeurs associées de type Boolean.|  
  
### <a name="value-attribute"></a>valeur d’attribut  
  
|Value|Description|  
|-----------|-----------------|  
|« nom = valeur »|Un nom de commutateur prédéfinis ainsi que sa valeur (`true` ou `false`). Plusieurs paires nom/valeur de commutateur sont séparés par des points-virgules (« ; »). Pour obtenir la liste de noms prédéfinis de commutateur pris en charge par le .NET Framework, consultez la section Notes.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 En commençant par le .NET Framework 4.6, la `<AppContextSwitchOverrides>` élément dans un fichier de configuration autorise les appelants dotés d’une API pour déterminer si son application peut tirer parti des nouvelles fonctionnalités ou conserver la compatibilité avec les versions précédentes d’une bibliothèque. Par exemple, si le comportement d’une API a changé entre deux versions d’une bibliothèque, le `<AppContextSwitchOverrides>` élément permet aux appelants de cette API pour désactiver le nouveau comportement sur les versions qui prennent en charge les nouvelles fonctionnalités de la bibliothèque. Pour les applications qui appellent des API dans le .NET Framework, le `<AppContextSwitchOverrides>` élément peut également permettre aux appelants dont les applications ciblent une version antérieure du .NET Framework à adopter les nouvelles fonctionnalités si leur application s’exécute sur une version de .NET Framework qui inclut fonctionnalité.  
  
 Le `value` attribut de la `<AppContextSwitchOverrides>` élément se compose d’une chaîne unique qui se compose d’une ou plusieurs paires nom/valeur délimitée par des points-virgules.  Chaque nom identifie un commutateur de compatibilité, et sa valeur correspondante est une valeur booléenne (`true` ou `false`) qui indique si le commutateur est défini. Par défaut, le commutateur est `false`, et les bibliothèques fournissent la nouvelle fonctionnalité. Ils fournissent uniquement les fonctionnalités antérieures si le commutateur est défini (autrement dit, sa valeur est `true`). Cela permet aux bibliothèques fournir le nouveau comportement d’API existantes tout en permettant aux appelants qui varient selon le comportement précédent refuser les nouvelles fonctionnalités.  
  
 Le .NET Framework prend en charge les commutateurs suivants :  
  
|Nom du commutateur|Description|Introduites|  
|-----------------|-----------------|----------------|  
|`Switch.MS.Internal.`<br/>`DoNotApplyLayoutRoundingToMarginsAndBorderThickness`|Détermine si Windows Presentation Foundation utilise hérité d’un algorithme pour la disposition des contrôles. Pour plus d’informations, consultez [Atténuation : disposition WPF](~/docs/framework/migration-guide/mitigation-wpf-layout.md).|.NET Framework 4.6|  
|`Switch.MS.Internal.`<br/>`UseSha1AsDefaultHashAlgorithmForDigitalSignatures`|Contrôle si l’algorithme par défaut utilisé pour la signature des parties d’un package par PackageDigitalSignatureManager est SHA1 ou SHA256.|.NET Framework 4.7.1|
|`Switch.System.Activities.`<br/>`UseMD5CryptoServiceProviderForWFDebugger`|Lorsque la valeur `false`, autorise le débogage de projets de workflow basé sur XAML avec Visual Studio lorsque FIPS est activé. Sans cela, un <xref:System.NullReferenceException> est levée dans les appels aux méthodes dans l’assembly System.Activities.|.NET Framework 4.7|
|`Switch.System.Activities.`<br/>`UseMD5ForWFDebugger`|Détermine si la somme de contrôle pour une instance de flux de travail dans le débogueur utilise MD5 ou SHA1. | .NET Framework 4.7|
|`Switch.System.Drawing.`<br/>`DontSupportPngFramesInIcons`|Contrôle si le <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> méthode lève une exception lorsqu’une <xref:System.Drawing.Icon> objet comporte des cadres PNG. Pour plus d’informations, consultez [Atténuation : cadres PNG dans les objets Icon](~/docs/framework/migration-guide/mitigation-png-frames-in-icon-objects.md).|.NET Framework 4.6|  
|`Switch.System.Globalization.NoAsyncCurrentCulture`|Contrôle si les opérations asynchrones ne sont pas acheminées à partir du contexte du thread de l’appelant. Pour plus d’informations, consultez [CurrentCulture et CurrentUICulture transmettent entre les tâches](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#currentculture-and-currentuiculture-flow-across-tasks).|.NET Framework 4.6|  
|`Switch.System.IdentityModel.`<br/>`DisableMultipleDNSEntriesInSANCertificate`|Contrôle si le <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> méthode tente de faire correspondre le type de revendication uniquement avec la dernière entrée DNS. Pour plus d’informations, consultez [Atténuation : X509CertificateClaimSet.FindClaims (méthode)](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.BlockLongPaths`|Contrôles si plus de chemins d’accès `MAX_PATH` (260 caractères) lèvent une <xref:System.IO.PathTooLongException>. Pour plus d’informations, consultez [prise en charge de Long chemin d’accès](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#long-path-support).|.NET Framework 4.6.2|  
|`Switch.System.IO.Compression.ZipFile.`<br/>`UseBackslash`|Utilise la barre oblique inverse («\\») au lieu de la barre oblique (« / ») comme séparateur de chemin d’accès dans le <xref:System.IO.Compression.ZipArchiveEntry.FullName%2A?displayProperty=nameWithType> propriété. Pour plus d’informations, consultez [atténuation : séparateur de chemin d’accès ZipArchiveEntry.FullName](~/docs/framework/migration-guide/mitigation-ziparchiveentry-fullname-path-separator.md).|.NET Framework 4.6.1|  
|`Switch.System.IO.Ports.`<br/>`DoNotCatchSerialStreamThreadExceptions`|Détermine si le fonctionnement des exceptions système qui sont levées sur les threads d’arrière-plan créés avec <xref:System.IO.Ports.SerialPort> flux mettre fin au processus.|.NET Framework 4.7.1| 
|`Switch.System.IO.`<br/>`UseLegacyPathHandling`|Détermine si la normalisation du chemin d’accès hérité est utilisée et les chemins d’accès de l’URI sont pris en charge par le <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=nameWithType> et <xref:System.IO.Path.GetPathRoot%2A?displayProperty=nameWithType> méthodes. Pour plus d’informations, consultez [atténuation : chemin d’accès de normalisation](~/docs/framework/migration-guide/mitigation-path-normalization.md) et [atténuation : vérifie des deux-points de chemin d’accès](~/docs/framework/migration-guide/mitigation-path-colon-checks.md).|.NET Framework 4.6.2|  
|`Switch.System.`<br/>`MemberDescriptorEqualsReturnsFalseIfEquivalent`|Détermine si un test d’égalité compare le <xref:System.ComponentModel.MemberDescriptor.Category%2A?displayProperty=nameWithType> propriété d’un objet avec le <xref:System.ComponentModel.MemberDescriptor.Description%2A?displayProperty=nameWithType> propriété du deuxième objet. Pour plus d’informations, consultez [implémentation incorrecte de MemberDescriptor.Equals](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#incorrect-implementation-of-memberdescriptorequals).|.NET Framework 4.6.2|  
 `Switch.System.Net.`<br/>`DontCheckCertificateEKUs`|Désactive la validation d’utilisation de clé améliorée (EKU) objet (OID) d’identificateur des certificats. Une extension de l’utilisation de clé améliorée (EKU) est une collection d’identificateurs d’objet (OID) qui indiquent les applications qui utilisent la clé.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchSendAuxRecord`|Désactive l’atténuation de TLS 1.0 navigateur exploiter par rapport à SSL/TLS (BEAST) en désactivant l’utilisation de SCH_SEND_AUX_RECORD.|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSchUseStrongCrypto`|Contrôle si le <xref:System.Net.ServicePointManager?displayProperty=nameWithType> et <xref:System.Net.Security.SslStream?displayProperty=nameWithType> les classes peuvent utiliser le protocole SSL 3.0. Pour plus d’informations, consultez [Atténuation : protocoles TLS](~/docs/framework/migration-guide/mitigation-tls-protocols.md).|.NET Framework 4.6|
|`Switch.System.Net.`<br/>`DontEnableSystemDefaultTlsVersions`|Désactive le retour à la valeur par défaut est Tls12, Tls11, Tls des versions SystemDefault TLS.|.NET Framework 4.7|
|`Switch.System.Net.`<br/>`DontEnableTlsAlerts`|Désactive les alertes du côté serveur SslStream TLS.|.NET Framework 4.7|
|`Switch.System.Runtime.Serialization.`<br/>`DoNotUseECMAScriptV6EscapeControlCharacter` |Contrôle si le [DataContractJsonSerializer](xref:System.Runtime.Serialization.Json.DataContractJsonSerializer) sérialise certains caractères de contrôle selon les normes ECMAScript V6 et V8. Pour plus d’informations, consultez [Atténuation : Sérialisation des caractères de contrôle avec DataContractJsonSerializer | Microsoft Docs](Mitigation:%20Serialization%20of%20Control%20Characters%20with%20the%20DataContractJsonSerializer.md)| .NET Framework 4.7 |
|`Switch.System.Security.ClaimsIdentity.`<br/>`SetActorAsReferenceWhenCopyingClaimsIdentity`|Contrôle si le <xref:System.Security.Claims.ClaimsIdentity.%23ctor%28System.Security.Principal.IIdentity%29?displayProperty=nameWithType> constructeur définit le nouvel objet <xref:System.Security.Claims.ClaimsIdentity.Actor%2A?displayProperty=nameWithType> propriété avec une référence d’objet existant. Pour plus d’informations, consultez [Atténuation : Constructeur ClaimsIdentity](~/docs/framework/migration-guide/mitigation-claimsidentity-constructor.md).|.NET Framework 4.6.2|  
|`Switch.System.Security.Cryptography.`<br/>`AesCryptoServiceProvider.DontCorrectlyResetDecryptor`|Contrôles si la tentative de réutiliser une <xref:System.Security.Cryptography.AesCryptoServiceProvider> déchiffreur lève une <xref:System.Security.Cryptography.CryptographicException>. Pour plus d’informations, consultez AesCryptoServiceProvider déchiffreur fournit un transform](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#aescryptoserviceprovider-decryptor-provides-a-reusable-transform) réutilisable.|.NET Framework 4.6.2|
|`Switch.System.Security.Cryptography.`<br/>`DoNotAddrOfCspParentWindowHandle`|Contrôle si la valeur de la [CspParameters.ParentWindowHandle](xref:System.Security.Cryptography.CspParameters.ParentWindowHandle) propriété est un [IntPtr](xref:System.IntPtr) que gérer les représente l’emplacement de mémoire d’une fenêtre, ou s’il s’agit d’un handle de fenêtre (HWND). Pour plus d’informations, consultez [Atténuation : CspParameters.ParentWindowHandle attend un HWND](Mitigation:%20CspParameters.ParentWindowHandle%20Expects%20an%20HWND.md). |.NET Framework 4.7|   
|`Switch.System.Security.Cryptography.Pkcs.`<br/>`UseInsecureHashAlgorithms`|Détermine si la valeur par défaut pour certaines opérations SignedCMS est SHA1 ou SHA256. |.NET Framework 4.7.1|
|`Switch.System.Security.Cryptography.Xml.`<br/>`UseInsecureHashAlgorithms`|Détermine si la valeur par défaut pour certaines opérations SignedXML est SHA1 ou SHA256. |.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`AllowUnsignedToHeader`|Détermine si le `TransportWithMessageCredential` mode de sécurité permet de messages avec un unsigned en-tête « to ». Il s’agit d’un commutateur opt-in. Pour plus d’informations, consultez [modifications du Runtime dans .NET Framework 4.6.1](https://msdn.microsoft.com/library/mt592686.aspx#WCF).|.NET Framework 4.6.1| 
|`Switch.System.ServiceModel.`<br/>`DisableAddressHeaderCollectionValidation`>|Contrôle si le <xref:System.ServiceModel.Channels.AddressHeaderCollection.%23ctor(System.Collections.Generic.IEnumerable{System.ServiceModel.Channels.AddressHeader})> constructeur lève une <xref:System.ArgumentException> si un des éléments est `null`.|.NET Framework 4.7.1| 
|`Switch.System.ServiceModel.`<br />`DisableCngCertificates`|Détermine que si la tentative d’utilisation X509 certificats avec un fournisseur de stockage de clés CSG lève une exception. Pour plus d’informations, consultez [sécurité du transport WCF prend en charge les certificats stockés à l’aide de CNG](~/docs/framework/migration-guide/retargeting/4.6.1-4.6.2.md#wcf-transport-security-supports-certificates-stored-using-cng).|.NET Framework 4.6.1|
|`Switch.System.ServiceModel.`<br/>`DisableOperationContextAsyncFlow`|Gère les blocages qui résultent de la restriction des instances d’un service réentrant à un seul thread d’exécution à la fois.|.NET Framework 4.6.2|
|`Switch.System.ServiceModel.`<br/>`DisableUsingServicePointManagerSecurityProtocols`|Avec `Switch.System.Net.DontEnableSchUseStrongCrypto`, détermine si la sécurité de message WCF utilise TLS 1.1 et TLS 1.2.|.NET Framework 4.7 |    
|`Switch.System.ServiceModel.`<br/>`UseSha1InMsmqEncryptionAlgorithm`|Détermine si le message par défaut la signature d’algorithme pour les messages MSMQ dans WCF est SHA1 ou SHA256.|.NET Framework 4.7.1|
|`Switch.System.ServiceModel.`<br/>`UseSha1InPipeConnectionGetHashAlgorithm`|Contrôle si WCF utilise un SHA1 ou un hachage SHA256 pour générer des noms aléatoires pour les canaux nommés.|.NET Framework 4.7.1|
|`Switch.System.ServiceProcess.`<br/>`DontThrowExceptionsOnStart`|Contrôle si les exceptions levées au démarrage du service sont propagées à l’appelant de la <xref:System.ServiceProcess.ServiceBase.Run%2A?displayProperty=nameWithType> (méthode).|.NET Framework 4.7.1|
|`Switch.System.Windows.Controls.Grid.`<br/>`StarDefinitionsCanExceedAvailableSpace` |Détermine si Windows Presentation Foundation s’applique à un ancien algorithme (`true`) ou un nouvel algorithme (`false`) lors de l’allocation d’espace pour \*-colonnes. Pour plus d’informations, consultez [Atténuation : Allocation d’espace du contrôle de grille à des colonnes en étoile](Mitigation:%20Grid%20Control's%20Space%20Allocation%20to%20Star-columns.md). |.NET Framework 4.7 |
|`Switch.System.Windows.Controls.TabControl.`<br/>`SelectionPropertiesCanLagBehindSelectionChangedEvent`|Événement modifié de contrôles si un sélecteur ou un onglet de contrôle toujours met à jour la valeur de sa propriété de valeur sélectionnée avant le déclenchement de la sélection.|.NET Framework 4.7.1|
|`Switch.System.Windows.Forms.`<br />`DontSupportReentrantFilterMessage`|Exclut le code qui permet une personnalisée <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> mise en œuvre en toute sécurité filtrer les messages sans lever d’exception lorsque la <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> méthode est appelée. Pour plus d’informations, consultez [Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées](~/docs/framework/migration-guide/mitigation-custom-imessagefilter-prefiltermessage-implementations.md).|.NET Framework 4.6.1|  
|`Switch.System.Windows.Input.Stylus.`<br/>`EnablePointerSupport`|Détermine si une option `WM_POINTER`-pile d’en fonction tactile/stylet est activée dans les applications WPF. Pour plus d’informations, consultez [atténuation : pointeur tactile et prise en charge du stylet](Mitigation:%20Pointer-based%20Touch%20and%20Stylus%20Support.md) | 
|`Switch.System.Windows.Media.ImageSourceConverter.`<br/>`OverrideExceptionWithNullReferenceException`|Détermine si un héritage [NullReferenceException](xref:System.NullReferenceException) est levée au lieu de l’exception qui indique plus spécifiquement la cause de l’exception (comme un [DirectoryNotFoundException](xref:System.IO.DirectoryNotFoundException) ou un [ FileNotFoundException](xref:System.IO.FileNotFoundException). Il est destiné par le code qui dépend de la gestion du [NullReferenceException](xref:System.NullReferenceException). | .NET Framework 4.7 |
|`Switch.UseLegacyAccessibilityFeatures`|Contrôle si les fonctionnalités d’accessibilité disponibles à partir du .NET Framework 4.7.1 est activées ou désactivées. | .NET Framework 4.7.1 |
|`System.Xml.`<br /><br /> `IgnoreEmptyKeySequences`|Contrôle si les séquences de touches vides dans les clés composées sont ignorés par la validation de schéma XSD. Pour plus d’informations, consultez [atténuation : Validation de schéma XML](~/docs/framework/migration-guide/mitigation-xml-schema-validation.md).|.NET Framework 4.6|  
  
> [!NOTE]
>  Au lieu d’ajouter un `AppContextSwitchOverrides` élément à un fichier de configuration d’application, vous pouvez également définir les commutateurs par programme en appelant le `static` (en c#) ou `Shared` (en Visual Basic) <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> (méthode).  
  
 Les développeurs de bibliothèques peuvent également définir des commutateurs pour autoriser les appelants à refuser la fonctionnalité modifiée introduite dans les versions ultérieures de leurs bibliothèques. Pour plus d'informations, consultez la classe <xref:System.AppContext>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `AppContextSwitchOverrides` élément pour définir un commutateur de compatibilité d’applications, `Switch.System.Globalization.NoAsyncCurrentCulture`, qui empêche le culture circulant entre les threads dans les appels de méthode asynchrone.  
  
```xml  
<configuration>  
   <runtime>  
      <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
   </runtime>  
</configuration>  
```  
  
 L’exemple suivant utilise le `AppContextSwitchOverrides` élément pour définir les deux commutateurs de compatibilité d’application, `Switch.System.Globalization.NoAsyncCurrentCulture` et `Switch.System.IO.BlockLongPaths`. Notez qu’un point-virgule sépare deux paires nom/valeur.  
  
```xml  
<configuration>  
    <runtime>  
       <AppContextSwitchOverrides   
          value="Switch.System.Globalization.NoAsyncCurrentCulture=true;Switch.System.IO.BlockLongPaths=true" />  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.AppContext?displayProperty=nameWithType>  
 [\<runtime > élément](runtime-element.md)  
 [\<configuration>, élément](../configuration-element.md)
