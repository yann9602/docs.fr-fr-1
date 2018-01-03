---
title: SqlClient pour Entity FrameworkTypes
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
caps.latest.revision: "9"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b04a7199fefc5df93d5e3472163d16c66e9279c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sqlclient-for-entity-frameworktypes"></a>SqlClient pour Entity FrameworkTypes
Le fichier de manifeste du fournisseur de données .NET Framework pour SQL Server (SqlClient) inclut la liste des types primitifs du fournisseur, les facettes de chaque type, les mappages entre les types primitifs des modèles conceptuels et de stockage, ainsi que les règles de promotion et de conversion entre les types primitifs des modèles conceptuels et de stockage.  
  
 Le tableau suivant décrit les types pour SQL Server 2008, [!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)], et [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)] types de modèles de bases de données et la façon dont ces types sont mappés à conceptuel. Certains nouveaux types introduits dans les versions ultérieures de SQL Server ne sont pas pris en charge dans les versions antérieures de SQL Server. Ces types sont signalés dans le tableau ci-dessous.  
  
|Type de fournisseur<br /><br /> name|Type de fournisseur<br /><br /> attributs|`EDMSimpleType`<br /><br /> name|Facettes|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|N/A|`Edm.Boolean`|N/A|  
|`tinyint`|N/A|`Edm.Byte`|N/A|  
|`smallint`|N/A|`Edm.Int16`|N/A|  
|`int`|N/A|`Edm.Int32`|N/A|  
|`bigint`|N/A|`Edm.Int64`|N/A|  
|`float`|N/A|`Edm.Double`|N/A|  
|`real`|N/A|`Edm.Double`|N/A|  
|`decimal`|N/A|`Edm.Decimal`|Précision :<br /><br /> -Minimale : 1<br /><br /> -Maximum : 38<br /><br /> -Par défaut : 18<br /><br /> -Constant : False<br /><br /> Mise à l’échelle :<br /><br /> -Minimale : 0<br /><br /> -Maximum : 38<br /><br /> -Par défaut : 0<br /><br /> -Constant : False|  
|`numeric`|N/A|`Edm.Decimal`|Précision :<br /><br /> -Minimale : 1<br /><br /> -Maximum : 38<br /><br /> -Par défaut : 18<br /><br /> -Constant : False<br /><br /> Mise à l’échelle :<br /><br /> -Minimale : 0<br /><br /> -Maximum : 38<br /><br /> -Par défaut : 0<br /><br /> -Constant : False|  
|`smallmoney`|N/A|`Edm.Decimal`|Précision :<br /><br /> -Par défaut : 10<br /><br /> -Constante : True<br /><br /> Mise à l’échelle :<br /><br /> -Par défaut : 4<br /><br /> -Constante : True|  
|`money`|N/A|`Edm.Decimal`|Précision :<br /><br /> -Par défaut : 19<br /><br /> -Constante : True<br /><br /> Mise à l’échelle :<br /><br /> -Par défaut : 4<br /><br /> -Constante : True|  
|`binary`|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Minimale : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constant : False<br /><br /> FixedLength :<br /><br /> -Par défaut : True<br /><br /> -Constante : True|  
|`varbinary`|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Minimale : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constant : False<br /><br /> FixedLength :<br /><br /> -Par défaut : False<br /><br /> -Constante : True|  
|`varbinary(max)`<br /><br /> Remarque : Ce type n’est pas pris en charge dans [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Par défaut : 214748364780<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : False<br /><br /> -Constante : True|  
|`image`|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Par défaut : 2147483647<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : False<br /><br /> -Constante : True|  
|`timestamp`|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Par défaut : 8<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : True<br /><br /> -Constante : True|  
|`rowversion`|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Par défaut : 8<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : True<br /><br /> -Constante : True|  
|`smalldatetime`|N/A|`Edm.DateTime`|Précision :<br /><br /> -Par défaut : 0<br /><br /> -Constante : True|  
|`datetime`|N/A|`Edm.DateTime`|Précision :<br /><br /> -Par défaut : 3<br /><br /> -Constante : True|  
|`date`<br /><br /> Remarque : Ce type n’est pas prise en charge dans SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTime`|Précision :<br /><br /> -Par défaut : 0<br /><br /> -Constant : False|  
|`time`<br /><br /> Remarque : Ce type n’est pas prise en charge dans SQL Server 2005 et SQL Server 2000.|N/A|`Edm.Time`|Précision :<br /><br /> -Par défaut : 7<br /><br /> -Constant : False|  
|`datetime2`<br /><br /> Remarque : Ce type n’est pas prise en charge dans SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTime`|Précision :<br /><br /> -Par défaut : 7<br /><br /> -Constant : False|  
|`datetimeoffset`<br /><br /> Remarque : Ce type n’est pas prise en charge dans SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTimeOffset`|Précision :<br /><br /> -Par défaut : 7<br /><br /> -Constant : False|  
|`nvarchar`<br /><br /> Remarque : Ce type n’est pas pris en charge dans [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|N/A|`Edm.String`|MaxLength :<br /><br /> -Minimale : 1<br /><br /> -Maximum : 4000<br /><br /> -Par défaut : 4000<br /><br /> -Constant : False<br /><br /> Unicode :<br /><br /> -Par défaut : True<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : False<br /><br /> -Constante : True|  
|`varchar`<br /><br /> Remarque : Ce type n’est pas pris en charge dans [!INCLUDE[ssVersion2000](../../../../../includes/ssversion2000-md.md)].|N/A|`Edm.String`|MaxLength :<br /><br /> -Minimale : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constant : False<br /><br /> Unicode :<br /><br /> -Par défaut : False<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : False<br /><br /> -Constante : True|  
|`char`|N/A|`Edm.String`|MaxLength :<br /><br /> -Minimale : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constant : False<br /><br /> Unicode :<br /><br /> -Par défaut : False<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : True<br /><br /> -Constante : True|  
|`nchar`|N/A|`Edm.String`|MaxLength :<br /><br /> -Minimale : 1<br /><br /> -Maximum : 4000<br /><br /> -Par défaut : 4000<br /><br /> -Constant : False<br /><br /> Unicode :<br /><br /> -Par défaut : True<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : True<br /><br /> -Constante : True|  
|`varchar`(`max`)|N/A|`Edm.String`|MaxLength :<br /><br /> -Par défaut : 2147483647<br /><br /> -Constante : True<br /><br /> Unicode :<br /><br /> -Par défaut : False<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : False<br /><br /> -Constante : True|  
|`nvarchar`(`max`)|N/A|`Edm.String`|MaxLength :<br /><br /> -Par défaut : 1073741823<br /><br /> -Constante : True<br /><br /> Unicode :<br /><br /> -Par défaut : True<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : False<br /><br /> -Constante : True|  
|`ntext`|Égal comparable : False<br /><br /> Comparable en ordre : False|`Edm.String`|MaxLength :<br /><br /> -Par défaut : 1073741823<br /><br /> -Constante : True<br /><br /> Unicode :<br /><br /> -Par défaut : False<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : False<br /><br /> -Constante : True|  
|`text`|Égal comparable : False<br /><br /> Comparable en ordre : False|`Edm.String`|MaxLength :<br /><br /> -Par défaut : 2147483647<br /><br /> -Constante : True<br /><br /> Unicode :<br /><br /> -Par défaut : False<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : False<br /><br /> -Constante : True|  
|`Unique`<br /><br /> `identifier`|Égal comparable : True<br /><br /> Comparable en ordre : True|`Edm.Guid`|N/A|  
|`xml`|Égal comparable : False<br /><br /> Comparable en ordre : False|`Edm.String`|MaxLength :<br /><br /> -Par défaut : 1073741823<br /><br /> -Constante : True<br /><br /> Unicode :<br /><br /> -Par défaut : True<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Par défaut : False<br /><br /> -Constante : True|  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifications CSDL, SSDL et MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
