# Serialization Example

At first lets create object that we will serialize / deserialize :

public class Rectangle implements Serializable{
    private double height;
    private double width;
    public Rectangle(double height, double width)
    {
        this.height = height;
        this.width = width;
    }
    public double area()
    {
        return height * width;
    }
    public double perimeter()
    {
        return 2 * (height + width);
    }
}

- than create object Rectangle rect = new Rectangle(18, 78); and write it to file
            // Step 1: Open a file output stream to create a file object on disk.
            // This file object will be used to write the serialized bytes of an object
            FileOutputStream fileStream = new FileOutputStream(fileName);

            // Step 2: Create a ObjectOutputStream, this class takes a files stream.
            // This class is responsible for converting the Object of any type into
            // a byte stream
            ObjectOutputStream objectStream = new ObjectOutputStream(fileStream);

            // Step 3: ObjectOutputStream.writeObject method takes an Object and
            // converts it into a ByteStream. Then it writes the Byte stream into
            // the file using the File stream that we created in step 1.
            objectStream.writeObject(classObject);

            // Step 4: Gracefully close the streams
            objectStream.close();
            fileStream.close();
after we can find our file with byte value = �� sr serialize.Rectangle����Y�L D heightD widthxp@2      @S�     

- than lets deserialize it again to object  ->    Rectangle deSerializedRect = (Rectangle) DeSerializeFromFileToObject(filePath);
DeSerializeFromFileToObject method will looks like : 
    public static Object DeSerializeFromFileToObject(String fileName){
            FileInputStream fileStream = new FileInputStream(new File(fileName));
            // Step 2: Create an object stream from the file stream. So that the content
            // of the file is converted to the Rectangle Object instance
            ObjectInputStream objectStream = new ObjectInputStream(fileStream);
            // Step 3: Read the content of the stream and convert it into object
            Object deserializeObject = objectStream.readObject();
            // Step 4: Close all the resources
            objectStream.close();
            fileStream.close();
            // return the deserialized object
            return object;
            }
