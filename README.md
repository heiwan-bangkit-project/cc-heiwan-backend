# Heiwan API List and How to Use It

/get-animals
method: GET
This is used to GET all the animals available from the database. This code block is using pagination

/products
method: GET
This method is used to GET all the products available from the seller. This code block is used to GET the products based on the seller's ID

/get-animal
method: GET
This method is used to GET available animal based by ID. If the ID isn't available, the code will return message "Animal not found"

/get-animal-by-name'
method: GET
This method is used to GET available animal based by name. If the name isn't available, the code will return message "Animal not found". This code blok is using pagination
Example param:
{
  name: Kucing
  page: page
}

/store-animal
method: POST
This method is used to POST animal into the database. You need to fill the name, descrption, and image (price can be null). If you didn't fill one of the data, the code
will return error message
Example param:
{
  name: Dog
  Description: Dog's description
  image: image link from Cloud Storage (since the API, Database, and Cloud Storage are integrated)
  price: 100000
}

/update-animal
method: POST
This method is used to update the animal information (database). Of course same like before, you need to fill the name, descrption, and image (price can be null). 
If you didn't fill one of the data, the code will return error message
Example param:
{
  animal_id: 1
  name: Black Doggo
  Description: Updated Dog's description
  image: Updated image link from Cloud Storage (since the API, Database, and Cloud Storage are integrated)
  price: 150000
}

/delete-animal
method: POST
This method will delete the animal. Why the method is POST? Of course because we use soft delete method. Data is important you know. We can analyze and export it
before we delete it permanently from the database. This delete method is based by animal's ID and will change the field deleted_at to be not null in the database 
(every animal displayed on the app have deleted_at field as not null)

/get-seller
method: GET
This method will GET the seller data and used to display the seller to the user in the app. The seller data is based on the seller ID. We get the seller data from 
Firebase auth and input it automatically to our database with /store-seller

/store-seller
method: POST
This method is used to input the seller data from Firebase auth.
Example data:
{
  uuid: SHihafkAHSF
  name: John Doe
  email: example@gmail.com
  phone: +62123456789
}

/update-seller
method: POST
This method is used to update the seller data.
Example data:
{
  name: Mr. John Doe 
  email: example1@gmail.com
  phone: +621234567890
}

/pred
This block is used to start image recognition. The "main.py" will start resizing the photo uploaded by user and start the image prediction by sending it to the
tfserving. And then tfserving will process it and give the result back to the API. Then after that, the API will give the result and display it to the user in the app

In this project, we just use one VM instance (Compute Engine). Inside this Compute Engine, there are Docker installerd to serve the tfserving models. There are also the
database to save the data (animals and sellers). We also use Cloud Storage to save the photo of the animal uploaded by the user, so the app can display it via 
Google Cloud Storage service account integrated with the backend

# CC Teams C024DSX1613, C169DSY3331 
