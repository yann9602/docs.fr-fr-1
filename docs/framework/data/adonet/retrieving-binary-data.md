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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b32002b8bb9b1eaf7a72a8fac306ecdd5f2e5931
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="retrieving-binary-data"></a><span data-ttu-id="eef43-102">Extraction de données binaires</span><span class="sxs-lookup"><span data-stu-id="eef43-102">Retrieving Binary Data</span></span>
<span data-ttu-id="eef43-103">Par défaut, le **DataReader** charge les données entrantes comme une ligne dès qu’une ligne de données complète est disponible.</span><span class="sxs-lookup"><span data-stu-id="eef43-103">By default, the **DataReader** loads incoming data as a row as soon as an entire row of data is available.</span></span> <span data-ttu-id="eef43-104">Les objets binaires volumineux ou BLOB doivent néanmoins être traités différemment car ils peuvent renfermer plusieurs gigaoctets de données qu'une seule ligne ne suffirait pas à contenir.</span><span class="sxs-lookup"><span data-stu-id="eef43-104">Binary large objects (BLOBs) need different treatment, however, because they can contain gigabytes of data that cannot be contained in a single row.</span></span> <span data-ttu-id="eef43-105">Le **Command.ExecuteReader** méthode a une surcharge qui prendra un <xref:System.Data.CommandBehavior> argument pour modifier le comportement par défaut de la **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="eef43-105">The **Command.ExecuteReader** method has an overload that will take a <xref:System.Data.CommandBehavior> argument to modify the default behavior of the **DataReader**.</span></span> <span data-ttu-id="eef43-106">Vous pouvez passer <xref:System.Data.CommandBehavior.SequentialAccess> à la **ExecuteReader** méthode permettant de modifier le comportement par défaut de la **DataReader** afin qu’au lieu de charger des lignes de données, il chargera les données séquentiellement qu’elles sont reçues.</span><span class="sxs-lookup"><span data-stu-id="eef43-106">You can pass <xref:System.Data.CommandBehavior.SequentialAccess> to the **ExecuteReader** method to modify the default behavior of the **DataReader** so that instead of loading rows of data, it will load data sequentially as it is received.</span></span> <span data-ttu-id="eef43-107">Cela est idéal pour charger les BLOB ou d'autres grosses structures de données.</span><span class="sxs-lookup"><span data-stu-id="eef43-107">This is ideal for loading BLOBs or other large data structures.</span></span> <span data-ttu-id="eef43-108">Notez que ce comportement peut différer selon votre source de données.</span><span class="sxs-lookup"><span data-stu-id="eef43-108">Note that this behavior may depend on your data source.</span></span> <span data-ttu-id="eef43-109">Par exemple, un BLOB retourné de Microsoft Access est entièrement chargé dans la mémoire, au lieu que les données soient chargées de façon séquentielle à mesure qu'elles arrivent.</span><span class="sxs-lookup"><span data-stu-id="eef43-109">For example, returning a BLOB from Microsoft Access will load the entire BLOB being loaded into memory, rather than sequentially as it is received.</span></span>  
  
 <span data-ttu-id="eef43-110">Lors de la définition du **DataReader** à utiliser **SequentialAccess**, il est important de noter l’ordre dans lequel vous accéder aux champs retournés.</span><span class="sxs-lookup"><span data-stu-id="eef43-110">When setting the **DataReader** to use **SequentialAccess**, it is important to note the sequence in which you access the fields returned.</span></span> <span data-ttu-id="eef43-111">Le comportement par défaut de la **DataReader**, qui charge une ligne entière dès qu’elle est disponible, vous permet d’accéder aux champs retournés dans n’importe quel ordre jusqu'à la lecture de la ligne suivante.</span><span class="sxs-lookup"><span data-stu-id="eef43-111">The default behavior of the **DataReader**, which loads an entire row as soon as it is available, allows you to access the fields returned in any order until the next row is read.</span></span> <span data-ttu-id="eef43-112">Lorsque vous utilisez **SequentialAccess** Toutefois, vous devez accéder les champs retournés par le **DataReader** dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="eef43-112">When using **SequentialAccess** however, you must access the fields returned by the **DataReader** in order.</span></span> <span data-ttu-id="eef43-113">Par exemple, si votre requête retourne trois colonnes, la troisième étant un BLOB, vous devez retourner les valeurs des premier et deuxième champs avant d'accéder aux données BLOB du troisième champ.</span><span class="sxs-lookup"><span data-stu-id="eef43-113">For example, if your query returns three columns, the third of which is a BLOB, you must return the values of the first and second fields before accessing the BLOB data in the third field.</span></span> <span data-ttu-id="eef43-114">Si vous accédez au troisième champ avant le premier ou le deuxième, les valeurs de ces champs ne seront plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="eef43-114">If you access the third field before the first or second fields, the first and second field values are no longer available.</span></span> <span data-ttu-id="eef43-115">C’est parce que **SequentialAccess** a modifié la **DataReader** pour retourner des données dans l’ordre et les données n’est pas disponible après la **DataReader** a.</span><span class="sxs-lookup"><span data-stu-id="eef43-115">This is because **SequentialAccess** has modified the **DataReader** to return data in sequence and the data is not available after the **DataReader** has read past it.</span></span>  
  
 <span data-ttu-id="eef43-116">Lorsque vous accédez aux données du champ BLOB, utilisez le **GetBytes** ou **GetChars** tapé les accesseurs de la **DataReader**, qui remplit un tableau avec les données.</span><span class="sxs-lookup"><span data-stu-id="eef43-116">When accessing the data in the BLOB field, use the **GetBytes** or **GetChars** typed accessors of the **DataReader**, which fill an array with data.</span></span> <span data-ttu-id="eef43-117">Vous pouvez également utiliser **GetString** pour les données de type caractère ; toutefois.</span><span class="sxs-lookup"><span data-stu-id="eef43-117">You can also use **GetString** for character data; however.</span></span> <span data-ttu-id="eef43-118">pour économiser les ressources système, vous souhaitez peut-être ne pas charger la valeur entière du BLOB dans une seule variable chaîne.</span><span class="sxs-lookup"><span data-stu-id="eef43-118">to conserve system resources you might not want to load an entire BLOB value into a single string variable.</span></span> <span data-ttu-id="eef43-119">Au lieu de cela, vous pouvez spécifier une taille de mémoire tampon spécifique des données à retourner ainsi qu'un emplacement de départ pour le premier octet ou le premier caractère lu des données retournées.</span><span class="sxs-lookup"><span data-stu-id="eef43-119">You can instead specify a specific buffer size of data to be returned, and a starting location for the first byte or character to be read from the returned data.</span></span> <span data-ttu-id="eef43-120">**GetBytes** et **GetChars** retournera un `long` valeur, qui représente le nombre d’octets ou de caractères retournés.</span><span class="sxs-lookup"><span data-stu-id="eef43-120">**GetBytes** and **GetChars** will return a `long` value, which represents the number of bytes or characters returned.</span></span> <span data-ttu-id="eef43-121">Si vous passez un tableau null à **GetBytes** ou **GetChars**, la valeur de type long retournée sera le nombre total d’octets ou de caractères dans l’objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="eef43-121">If you pass a null array to **GetBytes** or **GetChars**, the long value returned will be the total number of bytes or characters in the BLOB.</span></span> <span data-ttu-id="eef43-122">Vous pouvez éventuellement spécifier un index dans le tableau comme position de départ pour les données en cours de lecture.</span><span class="sxs-lookup"><span data-stu-id="eef43-122">You can optionally specify an index in the array as a starting position for the data being read.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eef43-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="eef43-123">Example</span></span>  
 <span data-ttu-id="eef43-124">L’exemple suivant retourne l’ID de l’éditeur et le logo de la **pubs** base de données dans Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="eef43-124">The following example returns the publisher ID and logo from the **pubs** sample database in Microsoft SQL Server.</span></span> <span data-ttu-id="eef43-125">L'ID de l'éditeur (`pub_id`) est un champ texte et le logo est une image (un BLOB).</span><span class="sxs-lookup"><span data-stu-id="eef43-125">The publisher ID (`pub_id`) is a character field, and the logo is an image, which is a BLOB.</span></span> <span data-ttu-id="eef43-126">Étant donné que la **logo** champ est une image bitmap, l’exemple retourne des données binaires à l’aide **GetBytes**.</span><span class="sxs-lookup"><span data-stu-id="eef43-126">Because the **logo** field is a bitmap, the example returns binary data using **GetBytes**.</span></span> <span data-ttu-id="eef43-127">Notez que pour la ligne de données actuelle, il faut accéder à l'ID de l'éditeur avant d'accéder au logo car l'accès aux champs doit être séquentiel.</span><span class="sxs-lookup"><span data-stu-id="eef43-127">Notice that the publisher ID is accessed for the current row of data before the logo, because the fields must be accessed sequentially.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eef43-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eef43-128">See Also</span></span>  
 [<span data-ttu-id="eef43-129">Utilisation de DataReaders</span><span class="sxs-lookup"><span data-stu-id="eef43-129">Working with DataReaders</span></span>](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="eef43-130">Données binaires et de valeur élevée SQL Server</span><span class="sxs-lookup"><span data-stu-id="eef43-130">SQL Server Binary and Large-Value Data</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="eef43-131">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="eef43-131">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
