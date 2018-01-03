---
title: REF CURSOR Oracle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 27351c1d47d4ad40940e5b64f257e6a59fc7403a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="oracle-ref-cursors"></a>REF CURSOR Oracle
Le fournisseur de données .NET Framework pour Oracle prend en charge Oracle **REF CURSOR** type de données. Lorsque vous utilisez le fournisseur de données pour travailler avec des REF CURSOR Oracle, vous devez tenir compte des comportements suivants.  
  
> [!NOTE]
>  Certains comportements diffèrent de ceux du fournisseur Microsoft OLE DB pour Oracle (MSDAORA).  
  
-   Pour des raisons de performances, le fournisseur de données pour Oracle ne lie pas automatiquement **REF CURSOR** types de données, comme le fait MSDAORA, sauf si vous les spécifiez explicitement.  
  
-   Le fournisseur de données ne prend pas en charge les séquences d'échappement ODBC, notamment l'échappement {resultset} utilisé pour spécifier les paramètres REF CURSOR.  
  
-   Pour exécuter une procédure stockée qui retourne les REF CURSOR, vous devez définir les paramètres dans le <xref:System.Data.OracleClient.OracleParameterCollection> avec un <xref:System.Data.OracleClient.OracleType> de **curseur** et un <xref:System.Data.OracleClient.OracleParameter.Direction%2A> de **sortie**. Le fournisseur de données prend en charge la liaison des REF CURSOR en tant que paramètres de sortie seulement. Le fournisseur ne prend pas en charge les REF CURSOR en tant que paramètres d'entrée.  
  
-   L'obtention d'un <xref:System.Data.OracleClient.OracleDataReader> à partir de la valeur de paramètre n'est pas prise en charge. Les valeurs sont de type <xref:System.DBNull> après l'exécution d'une commande.  
  
-   La seule **CommandBehavior** valeur d’énumération qui fonctionne avec des REF CURSOR (par exemple, lors de l’appel <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) est **CloseConnection**; tous les autres sont ignorés.  
  
-   L’ordre des REF CURSOR dans le **OracleDataReader** dépend de l’ordre des paramètres dans le **OracleParameterCollection**. La propriété <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> est ignorée.  
  
-   PL/SQL **TABLE** type de données n’est pas pris en charge. Toutefois, les REF CURSOR sont plus efficaces. Si vous devez utiliser un **TABLE** type de données, utilisez le fournisseur de données OLE DB .NET avec MSDAORA.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Exemples REF CURSOR](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 Contient trois exemples qui illustrent l'utilisation des REF CURSOR.  
  
 [Paramètres REF CURSOR dans un OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 Montre comment exécuter une procédure stockée PL/SQL qui retourne un paramètre REF CURSOR et lit la valeur comme un **OracleDataReader**.  
  
 [Récupération de données à partir de plusieurs REF CURSOR à l’aide d’un OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 Montre comment exécuter une procédure stockée PL/SQL qui retourne deux paramètres REF CURSOR et lit les valeurs en utilisant un **OracleDataReader**.  
  
 [Remplissage d’un DataSet à l’aide d’un ou de plusieurs REF CURSOR](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 Montre comment exécuter une procédure stockée PL/SQL qui retourne deux paramètres REF CURSOR et remplit un <xref:System.Data.DataSet> avec les lignes qui sont retournées.  
  
## <a name="see-also"></a>Voir aussi  
 [Oracle et ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
