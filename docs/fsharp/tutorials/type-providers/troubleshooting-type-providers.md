---
title: "Résolution des problèmes liés aux fournisseurs de type"
description: "Découvrez les solutions possibles pour les problèmes que vous êtes plus susceptible de rencontrer lorsque vous utilisez des fournisseurs de type en F #."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 44533045-9862-43c5-81d9-3e05157e975a
ms.openlocfilehash: 2b54454d7950dfdd6512d849fd739f505ef3317d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="troubleshooting-type-providers"></a>Résolution des problèmes liés aux fournisseurs de type

Cette rubrique décrit et fournit des solutions possibles pour les problèmes que vous êtes plus susceptible de rencontrer lorsque vous utilisez des fournisseurs de type.


## <a name="possible-problems-with-type-providers"></a>Identifier les problèmes éventuels des fournisseurs de Type
Si vous rencontrez un problème lorsque vous travaillez avec des fournisseurs de type, vous pouvez consulter le tableau suivant pour les solutions les plus courantes.



|Problème|Actions suggérées|
|-------|-----------------|
|**Modifications de schéma**. Tapez les fournisseurs fonctionnent mieux lorsque le schéma de source de données est stable. Si vous ajoutez une table de données ou une colonne ou que vous effectuez une modification supplémentaire à ce schéma, le fournisseur de type ne reconnaît pas automatiquement ces modifications.|Nettoyer ou régénérez le projet. Pour nettoyer le projet, choisissez **générer**, **Clean** *nom_projet* sur la barre de menus. Pour régénérer le projet, choisissez **générer**, **reconstruire** *nom_projet* sur la barre de menus. Ces actions réinitialise tous les États de fournisseur de type et de forcer le fournisseur à se reconnecter à la source de données et obtenir des informations de schéma mis à jour.|
|**Échec de connexion**. La chaîne de connexion ou d’URL est incorrecte, le réseau est hors service ou la source de données ou le service n’est pas disponible.|Pour un service web ou un service OData, vous pouvez essayer l’URL dans Internet Explorer pour vérifier si l’URL est correcte et que le service est disponible. Pour une chaîne de connexion de base de données, vous pouvez utiliser les outils de connexion de données dans **l’Explorateur de serveurs** pour vérifier si la chaîne de connexion est valide et que la base de données est disponible. Après avoir restauré votre connexion, vous devez ensuite nettoyer ou régénérez le projet afin que le fournisseur de type se reconnectera au réseau.|
|**Les informations d’identification non valides**. Vous devez disposer des autorisations correctes pour le service web ou de la source de données.|Pour une connexion SQL, le nom d’utilisateur et le mot de passe sont spécifiés dans le fichier de configuration ou de la chaîne de connexion doivent être valides pour la base de données. Si vous utilisez l’authentification Windows, vous devez avoir accès à la base de données. L’administrateur de base de données peut identifier les autorisations pour que nécessaires accéder à chaque base de données et chaque élément dans une base de données.<br /><br />Pour un service web ou un service de données, vous devez disposer des informations d’identification appropriées. La plupart des fournisseurs de type fournissent un objet DataContext, qui contient la propriété informations d’identification que vous pouvez définir avec le nom d’utilisateur et la clé d’accès.|
|**Chemin d’accès non valide**. Un chemin d’accès à un fichier n’est pas valide.|Vérifiez si le chemin d’accès est correct et que le fichier existe. En outre, vous devez placer entre guillemets de n’importe quel backlashes dans le chemin d’accès en conséquence ou utiliser une chaîne textuelle ou à guillemets triples.|

## <a name="see-also"></a>Voir aussi
[Fournisseurs de type](index.md)
