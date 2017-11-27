---
title: Interfaces du magasin de symboles de diagnostics
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 50ef54c90609bf8ef1e3a943664daef95f50d926
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="diagnostics-symbol-store-interfaces"></a>Interfaces du magasin de symboles de diagnostics
Cette rubrique décrit les interfaces non managées qui permettent un compilateur à générer des informations de symbole pour une utilisation par un débogueur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [IBindingDisplay (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 Fournit des méthodes qui affichent des informations de liaison en cours sur l’application en cours d’exécution.  
  
 [IDebugAutoAttach (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 Définit l’interface pour l’attachement automatique du débogueur appelé par serveur.  
  
 [INotifyConnection2 (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 Déclare des méthodes pour l’inscription et la désinscription d’une source de notification de connexion.  
  
 [INotifySink2 (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 Déclare des méthodes pour la notification de récepteur.  
  
 [INotifySource2 (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 Déclare une méthode pour définir des filtres de notification.  
  
 [ISymENCUnmanagedMethod (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 Fournit des informations pour la fonctionnalité Modifier & Continuer.  
  
 [Isymunmanagedasyncmethod, Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 Cette interface est le complément de la lecture à [isymunmanagedasyncmethodpropertieswriter, Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [Isymunmanagedasyncmethodpropertieswriter, Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Permet la définition d’informations sur la méthode async facultatif par le symbole de méthode. Doit utiliser avec une méthode ouverte (autrement dit, entre les appels à la [OpenMethod (méthode)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)et le [CloseMethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).  
  
 [ISymUnmanagedBinder (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 Représente un classeur de symboles pour le code non managé.  
  
 [ISymUnmanagedBinder2 (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 Représente un classeur de symboles pour le code non managé et étend la `ISymUnmanagedBinder` interface.  
  
 [ISymUnmanagedBinder3 (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 Représente un classeur de symboles pour le code non managé et étend la `ISymUnmanagedBinder` interface.  
  
 [ISymUnmanagedConstant (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 Fournit l’accès aux constantes non managées.  
  
 [ISymUnmanagedDispose (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 Libère les ressources non managées.  
  
 [ISymUnmanagedDocument (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 Représente un document référencé par un magasin de symboles.  
  
 [ISymUnmanagedDocumentWriter (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 Fournit des méthodes d'écriture dans un document référencé par un magasin de symboles.  
  
 [ISymUnmanagedENCUpdate (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 Fournit des méthodes pour la fonctionnalité Modifier & Continuer.  
  
 [ISymUnmanagedMethod (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 Représente une méthode dans le magasin de symboles.  
  
 [ISymUnmanagedNamespace (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 Représente un espace de noms.  
  
 [ISymUnmanagedReader (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 Représente un lecteur de symboles qui fournit l’accès aux documents, des méthodes et des variables dans un magasin de symboles.  
  
 [ISymUnmanagedReader2 (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 Obtient une méthode de lecteur de symboles étant donnée un jeton de méthode et un numéro de version de la modifier et copier.  
  
 [ISymUnmanagedReaderSymbolSearchInfo (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 Fournit des méthodes qui obtiennent des informations de la recherche de symbole.  
  
 [ISymUnmanagedScope (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 Représente une portée lexicale dans une méthode.  
  
 [ISymUnmanagedScope2 (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 Représente une portée lexicale dans une méthode et étend la `ISymUnmanagedScope` interface avec des méthodes qui obtiennent des informations sur les constantes définies dans l’étendue...  
  
 [ISymUnmanagedSourceServerModule (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 Fournit des données du serveur source pour un module.  
  
 [ISymUnmanagedSymbolSearchInfo (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 Fournit des méthodes qui obtiennent des informations sur le chemin de recherche.  
  
 [ISymUnmanagedVariable (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 Représente une variable, comme un paramètre, une variable locale ou un champ.  
  
 [ISymUnmanagedWriter (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 Représente un writer de symbole et fournit des méthodes pour définir des documents, les points de séquence, les portées lexicales et variables.  
  
 [ISymUnmanagedWriter2 (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 Représente un writer de symbole et fournit des méthodes pour définir des documents, les points de séquence, les portées lexicales et variables. Étend la `ISymUnmanagedWriter` interface.  
  
 [ISymUnmanagedWriter3 (Interface)](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 Représente un writer de symbole et fournit des méthodes pour définir des documents, les points de séquence, les portées lexicales et variables. Étend la `ISymUnmanagedWriter` interface.  
  
 [Isymunmanagedwriter4, Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 Isymunmanagedwriter4, interface.  
  
 [Isymunmanagedwriter5, Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 Isymunmanagedwriter5, interface.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Énumérations du magasin de symboles de Diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [Structures du magasin de symboles de Diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
