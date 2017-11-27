---
title: "Combinaison de protocoles d'approbation dans les scénarios fédérés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 007dec81766423ea2826e98ae0b6b399a1508f11
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Combinaison de protocoles d'approbation dans les scénarios fédérés
Il peut exister des scénarios où des clients fédérés communiquent avec un WSDL de service et un service de jeton de sécurité (STS) qui n'ont pas la même version d'approbation. Le WSDL de service peut contenir une assertion `RequestSecurityTokenTemplate` avec les éléments WS-Trust qui sont de versions différentes par rapport à STS. Dans ce cas, un client [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] convertit les éléments WS-Trust reçus depuis `RequestSecurityTokenTemplate` de façon à ce qu'ils correspondent à la version d'approbation de STS. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gère les versions d'approbation qui ne correspondent pas uniquement pour les liaisons standard. Tous les paramètres d'algorithme standard reconnus par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] font partie de la liaison standard. Cette rubrique décrit le comportement de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] avec divers paramètres d'approbation entre le service et STS.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP février 2005 et STS février 2005  
 Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Le fichier de configuration client contient une liste de paramètres.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne peut pas différencier les paramètres du client des paramètres du service ; il ajoute tous les paramètres et les envoie dans `RequestSecurityTokenTemplate` (RST).  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>Version d'approbation RP 1.3 et Version d'approbation STS 1.3  
 Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 Le fichier de configuration client contient un élément `secondaryParameters` qui encapsule les paramètres spécifié par la partie de confiance.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supprime les éléments `EncryptionAlgorithm`, `CanonicalizationAlgorithm` et `KeyWrapAlgorithm` de l'élément de niveau supérieur sous le RST si ceux-ci sont présents dans l'élément `SecondaryParameters`. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ajoute l'élément `SecondaryParameters` au RST sortant non modifié.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>Version d'approbation RP février 2005 et Version d'approbation STS 1.3  
 Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 Le fichier de configuration client contient une liste de paramètres.  
  
 À partir du fichier de configuration client, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ne peut pas différencier les paramètres du service de ceux du client. Par conséquent, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] convertit tous les paramètres en un espace de noms de version d'approbation 1.3.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gère les éléments `KeyType`, `KeySize` et `TokenType` comme suit :  
  
-   Téléchargez le WSDL, créez la liaison et assignez `KeyType`, `KeySize` et `TokenType` à partir des paramètres RP. Le fichier de configuration client est alors généré.  
  
-   Le client peut maintenant modifier tout paramètre dans le fichier de configuration.  
  
-   Pendant l'exécution, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copie tous les paramètres spécifiés dans la section `AdditionalTokenParameters` du fichier de configuration client sauf `KeyType`, `KeySize` et `TokenType` car ces paramètres sont pris en compte pendant la génération du fichier de configuration.  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>Version d'approbation RP 1.3 et Version d'approbation STS février 2005  
 Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 Le fichier de configuration client contient un élément `secondaryParamters` qui encapsule les paramètres spécifié par la partie de confiance.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copie tous les paramètres spécifiés dans la section `SecondaryParameters` dans l'élément RST de niveau supérieur, mais ne les convertit pas en espace de noms WS-Trust 2005.
