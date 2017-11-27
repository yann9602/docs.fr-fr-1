---
title: "Procédure pas à pas : accès à un Service Web à l’aide de fournisseurs de Type (F #)"
description: "Découvrez comment utiliser le fournisseur de type de Web Services Description Language (WSDL) disponible dans F # 3.0 pour accéder à un service WSDL."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 63374fa9-8fb8-43ac-bcb9-ef2290d9f851
ms.openlocfilehash: 06d955033d465cf58af05f483d21175f90d1777a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-web-service-by-using-type-providers"></a>Procédure pas à pas : accès à un service Web à l’aide des fournisseurs de type

> [!NOTE]
Ce guide a été écrit pour F # 3.0 et sera mise à jour.  Pour obtenir la liste la plus récente des fournisseurs de type multiplateformes, consultez [FSharp.Data](http://fsharp.github.io/FSharp.Data/).

> [!NOTE]
Les liens de référence d’API vous permettront de MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Cette procédure pas à pas montre comment utiliser le fournisseur de type Web Services Description Language (WSDL) n’est disponible dans F # 3.0 pour accéder à un service WSDL. Dans d’autres langages .NET, vous générez le code pour accéder au service web par svcutil.exe appelant, ou en ajoutant une référence web dans, par exemple, un projet c# pour obtenir Visual Studio pour appeler svcutil.exe pour vous. En F #, vous avez la possibilité supplémentaire de l’utilisation du fournisseur de type WSDL, par conséquent, dès que vous écrivez le code qui crée le type WsdlService, les types sont générés et sont disponibles. Ce processus s’appuie sur le service est disponible lorsque vous écrivez le code.

Cette procédure pas à pas décrit les tâches suivantes. Vous devez effectuer les dans cet ordre pour la procédure pas à pas réussisse :


- Création du projet
<br />

- Configuration du fournisseur de type
<br />

- Appel du service web et le traitement des résultats
<br />


## <a name="creating-the-project"></a>Création du projet
Dans l’étape, vous créez un projet et ajoutez les références appropriées pour utiliser un fournisseur de type WSDL.


#### <a name="to-create-and-set-up-an-f-project"></a>Pour créer et configurer le projet F#

1. Ouvrez un nouveau projet d’Application Console F #.
<br />

2. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet **référence** nœud, puis choisissez **ajouter une référence**.
<br />

3. Dans le **assemblys** zone, choisissez **Framework**, puis, dans la liste des assemblys disponibles, choisissez **System.Runtime.Serialization** et  **System.ServiceModel**.
<br />

4. Dans le **assemblys** zone, choisissez **Extensions**.
<br />

5. Dans la liste des assemblys disponibles, choisissez **FSharp.Data.TypeProviders**, puis choisissez le **OK** bouton pour ajouter des références aux assemblys suivants.
<br />

## <a name="configuring-the-type-provider"></a>Configuration du fournisseur de type
Dans cette étape, vous utilisez le fournisseur de type WSDL pour générer des types pour le service web de TerraServer.


#### <a name="to-configure-the-type-provider-and-generate-types"></a>Pour configurer le fournisseur de type et générer des types

1. Ajoutez la ligne suivante de code pour ouvrir l’espace de noms de fournisseur de type.
<br />

```fsharp
open System
open System.ServiceModel
open Microsoft.FSharp.Linq
open Microsoft.FSharp.Data.TypeProviders
```

2. Ajoutez la ligne suivante de code pour appeler le fournisseur de type avec un service web. Dans cet exemple, utilisez le service web TerraServer.
<br />

```fsharp
type TerraService = WsdlService<" HYPERLINK "http://terraserver-usa.com/TerraService2.asmx?WSDL" http://msrmaps.com/TerraService2.asmx?WSDL">
```

  Si l’URI de service est mal orthographié ou si le service est arrêté ou ne fonctionne pas, une ligne ondulée rouge s’affiche sous cette ligne de code. Si vous pointez sur le code, un message d’erreur décrit le problème. Vous pouvez obtenir les mêmes informations dans le **liste d’erreurs** fenêtre ou dans le **fenêtre sortie** après la génération.
<br />  Il existe deux façons de spécifier les paramètres de configuration pour une connexion de WSDL, à l’aide du fichier app.config pour le projet, ou en utilisant les paramètres de type statique dans la déclaration de fournisseur de type. Vous pouvez utiliser svcutil.exe pour générer des éléments de fichier de configuration approprié. Pour plus d’informations sur l’utilisation de svcutil.exe pour générer des informations de configuration pour un service web, consultez [ServiceModel Metadata Utility Tool &#40; SvcUtil.exe &#41; ](https://msdn.microsoft.com/library/aa347733.aspx). Pour obtenir une description complète des paramètres de type statique pour le fournisseur de type WSDL, consultez [fournisseur de Type WsdlService](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d).
<br />

## <a name="calling-the-web-service-and-processing-the-results"></a>Appel du service web et le traitement des résultats
Chaque service web a son propre ensemble de types qui sont utilisés en tant que paramètres pour ses appels de méthode. Dans cette étape, vous préparez ces paramètres, appelez une méthode web et traiter les informations qu’elle retourne.


#### <a name="to-call-the-web-service-and-process-the-results"></a>Pour appeler le service web et traiter les résultats

1. Le service web peut expirer ou cesser de fonctionner, donc vous devez inclure l’appel du service web dans une bloc de gestion des exceptions. Écrire le code suivant pour essayer d’obtenir des données à partir du service web.
<br />

```fsharp
try
  let terraClient = TerraService.GetTerraServiceSoap ()
  let myPlace = new TerraService.ServiceTypes.msrmaps.com.Place(City = "Redmond", State = "Washington", Country = "United States")
  let myLocation = terraClient.ConvertPlaceToLonLatPt(myPlace)
  printfn "Redmond Latitude: %f Longitude: %f" (myLocation.Lat) (myLocation.Lon)
with
| :? ServerTooBusyException as exn ->
  let innerMessage =
    match (exn.InnerException) with
    | null -> ""
    | innerExn -> innerExn.Message
  printfn "An exception occurred:\n %s\n %s" exn.Message innerMessage
| exn -> printfn "An exception occurred: %s" exn.Message
```

Notez que vous créez les types de données qui sont nécessaires pour le service web, tel que **Place** et **emplacement**, comme les types imbriqués sous la WsdlService de type **TerraService**.
<br />


## <a name="see-also"></a>Voir aussi
[Fournisseur de Type de WsdlService](https://msdn.microsoft.com/visualfsharpdocs/conceptual/wsdlservice-type-provider-%5bfsharp%5d)

[Fournisseurs de type](index.md)
