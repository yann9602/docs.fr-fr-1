---
title: Exemple FindPrivateKey - WCF
ms.date: 12/04/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 29489cd1b82cf1c31f178d8a305a21371b542f15
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2017
---
# <a name="findprivatekey-sample"></a>Exemple de FindPrivateKey

Il peut être difficile de rechercher l'emplacement et le nom du fichier de clé privée associé à un certificat X.509 spécifique dans le magasin de certificats. L'outil FindPrivateKey.exe facilite ce processus.

> [!IMPORTANT]
> FindPrivateKey est un exemple qui doit être compilé avant son utilisation. Consultez le [pour générer le projet FindPrivateKey](#to-build-the-findprivatekey-project) section pour obtenir des instructions sur la création de l’outil FindPrivateKey.

Les certificats X.509 sont installés par un administrateur ou tout utilisateur sur l'ordinateur. Toutefois, le certificat est accessible par un service en cours d’exécution sous un compte différent. Par exemple, le compte de SERVICE réseau.

Ce compte peut ne pas avoir accès au fichier de clé privée parce qu'il n'a pas installé le certificat à l'origine. L'outil FindPrivateKey vous donne l'emplacement du fichier de clé privée d'un certificat X.509 donné. Vous pouvez ajouter ou supprimer des autorisations à ce fichier une fois que vous connaissez l'emplacement du fichier de clé privée des certificats X.509 particuliers.

Les exemples qui utilisent des certificats de sécurité utilisent l’outil FindPrivateKey dans le *Setup.bat* fichier. Une fois que le fichier de clé privée a été trouvé, vous pouvez utiliser d’autres outils tels que *Cacls.exe* pour définir les droits d’accès appropriés sur le fichier.

Lors de l’exécution d’un service Windows Communication Foundation (WCF) sous un compte d’utilisateur, par exemple un fichier exécutable auto-hébergé, vérifiez que le compte d’utilisateur a accès en lecture seule au fichier. Lors de l’exécution d’un service WCF sous Internet Information Services (IIS) les comptes par défaut que le service s’exécute sous sont le SERVICE réseau sur IIS 7 et versions antérieures, ou identité de Pool d’applications dans IIS 7.5 et versions ultérieures. Pour plus d’informations, consultez [identités du Pool d’applications](/iis/manage/configuring-security/application-pool-identities).

## <a name="examples"></a>Exemples

Lorsque vous accédez à un certificat pour lequel le processus n’a le privilège de lecture, vous voyez un message d’exception similaire à l’exemple suivant :

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

Lorsque cela se produit, utilisez l’outil FindPrivateKey pour rechercher le fichier de clé privée, puis définissez le droit d’accès pour le service s’exécute sous le processus. Par exemple, cela est possible avec l’outil Cacls.exe comme indiqué dans l’exemple suivant :

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>Pour générer le projet FindPrivateKey

Pour télécharger le projet, visitez [Windows Communication Foundation (WCF) et des exemples Windows Workflow Foundation (WF) pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).

1. Ouvrez [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] et accédez à la *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* dossier sous l’emplacement du répertoire où vous avez installé l’exemple.

2. Double-cliquez sur l'icône du fichier .sln pour ouvrir ce dernier dans Visual Studio.

3. Dans le **générer** menu, sélectionnez **régénérer la Solution**.

4. La génération de la solution génère le fichier : FindPrivateKey.exe.

## <a name="conventionscommand-line-entries"></a>Conventions, les entrées de ligne de commande

 « [*option*] » représente un ensemble facultatif de paramètres.

 « {*option*} » représente un jeu obligatoire de paramètres.

 «*option1* &#124; *option2*« représente un choix entre des ensembles d’options.

 «\<*valeur*> » représente une valeur de paramètre doit être entré.

## <a name="usage"></a>Utilisation

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

Où :

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

Si aucun paramètre est spécifié à l’invite de commande, ce texte d’aide s’affiche.

## <a name="examples"></a>Exemples

Cet exemple recherche le nom de fichier du certificat avec le nom de sujet « CN = localhost », dans le magasin personnel de l’utilisateur actuel.

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

Cet exemple recherche le nom de fichier du certificat avec le nom de sujet « CN = localhost », le personnel stocker de l’utilisateur actuel et le chemin d’accès complet du répertoire de sortie.

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

Cet exemple recherche le nom de fichier du certificat avec l'empreinte numérique « 03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52 » dans le magasin personnel de l'ordinateur local.

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
