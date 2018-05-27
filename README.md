# Sign-language-dataset
This repository contains the code to re-train a machine learning model for image classifcation and the neccesarry labeled dataset.
The data is used to develop an application for deaf people, the app must recognize the hand gestures and translate them to text using the trained model. 

The code from this repo comes from a <a href="https://www.tensorflow.org/">Tensorflow</a> tutorial.

<ul>
   <li>retrain.py comes from: <a href="https://www.tensorflow.org/tutorials/image_retraining">source</a></li>
   <li>classi.py <i>(Get it!? <b>CLASSI.PY!!!</b> from classify!!!)</i> comes from: <a href="https://www.tensorflow.org/tutorials/image_recognition">source</a></li>
</ul>

## Dependencies
<ul>
   <li><a href="https://www.python.org/ftp/python/3.6.5/python-3.6.5-amd64.exe">Python 3.5.x or higher (64-bit version only) </a></li>
   <li>tensorflow <code>pip install tensorflow</code></li>
   <li>tensorboard <code>pip install tensorboard</code></li>
   <li>Other python libraries you might need te <code>pip install</code></li>
</ul>

## To run this example
Run the folowing commands:

<code>
python retrain.py --bottleneck_dir data/bottlenecks --model_dir data/inception --output_graph data/sign_language_graph.pb --output_labels data/sign_language_labels.txt --image_dir hand_images --summaries_dir retrain_logs
</code>



This command executes the retrain.py script, it takes 30-45 minutes. In bottlenecks the images are stored represented as numbers, the .pb file will be the data graph used to make predictions, in labels.txt the different labels stored(This can be changed later by hand).

This is how the image directory structure should like: (The name of the sub-folders is equivalent to the label names)

<ul>
   <li>hand_images</li>
   <li>
      <ul>
         <li>one</li>
         <li>
            <ul>
               <li>image.jpg</li>
               <li>image.jpg</li>
               <li>image.jpg</li>
               <li>image.jpg</li>
            </ul>
         </li>
      </ul>
   </li>
      <li>
      <ul>
         <li>two</li>
         <li>
            <ul>
               <li>image.jpg</li>
               <li>image.jpg</li>
               <li>image.jpg</li>
               <li>image.jpg</li>
            </ul>
         </li>
      </ul>
   </li>
      <li>
      <ul>
         <li>three</li>
         <li>
            <ul>
               <li>image.jpg</li>
               <li>image.jpg</li>
               <li>image.jpg</li>
               <li>image.jpg</li>
            </ul>
         </li>
      </ul>
   </li>
   
   <li>etc.</li>

</ul>



After that you can see the results on Tensorboard, with this command:

<code>
tensorboard --logdir retrain_logs
</code>


Now you can test the model with a random unlabled image: 

<code>
python classi.py --graph data/sign_language_graph.pb --labels data/sign_language_labels.txt --input_layer Placeholder --output_layer final_result --image <IMAGE>
</code>