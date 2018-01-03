---
title: "Extraction de données binaires"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 43e937836911808789e2cad8affb395cc73ceb68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="retrieving-binary-data"></a>Extraction de données binaires
Par défaut, le **DataReader** charge les données entrantes comme une ligne dès qu’une ligne de données complète est disponible. Les objets binaires volumineux ou BLOB doivent néanmoins être traités différemment car ils peuvent renfermer plusieurs gigaoctets de données qu'une seule ligne ne suffirait pas à contenir. Le **Command.ExecuteReader** méthode a une surcharge qui prendra un <xref:System.Data.CommandBehavior> argument pour modifier le comportement par défaut de la **DataReader**. Vous pouvez passer <xref:System.Data.CommandBehavior.SequentialAccess> à la **ExecuteReader** méthode permettant de modifier le comportement par défaut de la **DataReader** afin qu’au lieu de charger des lignes de données, il chargera les données séquentiellement qu’elles sont reçues. Cela est idéal pour charger les BLOB ou d'autres grosses structures de données. Notez que ce comportement peut différer selon votre source de données. Par exemple, un BLOB retourné de Microsoft Access est entièrement chargé dans la mémoire, au lieu que les données soient chargées de façon séquentielle à mesure qu'elles arrivent.  
  
 Lors de la définition du **DataReader** à utiliser **SequentialAccess**, il est important de noter l’ordre dans lequel vous accéder aux champs retournés. Le comportement par défaut de la **DataReader**, qui charge une ligne entière dès qu’elle est disponible, vous permet d’accéder aux champs retournés dans n’importe quel ordre jusqu'à la lecture de la ligne suivante. Lorsque vous utilisez **SequentialAccess** Toutefois, vous devez accéder les champs retournés par le **DataReader** dans l’ordre. Par exemple, si votre requête retourne trois colonnes, la troisième étant un BLOB, vous devez retourner les valeurs des premier et deuxième champs avant d'accéder aux données BLOB du troisième champ. Si vous accédez au troisième champ avant le premier ou le deuxième, les valeurs de ces champs ne seront plus disponibles. C’est parce que **SequentialAccess** a modifié la **DataReader** pour retourner des données dans l’ordre et les données n’est pas disponible après la **DataReader** a.  
  
 Lorsque vous accédez aux données du champ BLOB, utilisez le **GetBytes** ou **GetChars** tapé les accesseurs de la **DataReader**, qui remplit un tableau avec les données. Vous pouvez également utiliser **GetString** pour les données de type caractère ; toutefois. pour économiser les ressources système, vous souhaitez peut-être ne pas charger la valeur entière du BLOB dans une seule variable chaîne. Au lieu de cela, vous pouvez spécifier une taille de mémoire tampon spécifique des données à retourner ainsi qu'un emplacement de départ pour le premier octet ou le premier caractère lu des données retournées. **GetBytes** et **GetChars** retournera un `long` valeur, qui représente le nombre d’octets ou de caractères retournés. Si vous passez un tableau null à **GetBytes** ou **GetChars**, la valeur de type long retournée sera le nombre total d’octets ou de caractères dans l’objet BLOB. Vous pouvez éventuellement spécifier un index dans le tableau comme position de départ pour les données en cours de lecture.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant retourne l’ID de l’éditeur et le logo de la **pubs** base de données dans Microsoft SQL Server. L'ID de l'éditeur (`pub_id`) est un champ texte et le logo est une image (un BLOB). Étant donné que la **logo** champ est une image bitmap, l’exemple retourne des données binaires à l’aide **GetBytes**. Notez que pour la ligne de données actuelle, il faut accéder à l'ID de l'éditeur avant d'accéder au logo car l'accès aux champs doit être séquentiel.  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream                   
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter                 
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100        
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte    
' The bytes returned from GetBytes.  
Dim retval As Long                     
' The starting position in the BLOB output.  
Dim startIndex As Long = 0             
  
' The publisher id to use in the file name.  
Dim pubID As String = ""              
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;                            
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;                          
  
// Size of the BLOB buffer.  
int bufferSize = 100;                     
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];    
// The bytes returned from GetBytes.  
long retval;                              
// The starting position in the BLOB output.  
long startIndex = 0;                      
  
// The publisher id to use in the file name.  
string pubID = "";                       
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);    
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de DataReaders](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [Données binaires et de valeur élevée SQL Server](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
