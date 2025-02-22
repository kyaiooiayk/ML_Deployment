# Model Serialisation
***

## What is model serialisation?
- Serialisation is the process of translating a data structure or object state into a format that can be stored (for example, in a file or memory data buffer) or transmitted (for example, over a computer network) and reconstructed later (possibly in a different computer environment).
- In other words, serialising is a way to write a python object on the disk that can be transferred anywhere and later de-serialized (read) back by a python script.
- The reason for that is that the ML model iself should be rendered executable as an independent asset: a Scikit-learn model shoudl be run in a Spark job.  - Essentially, serialisation rended the model language-trained-agnostic and not vendor-specific.
***

## Available formats
- **Sklearn** recommends using the `joblib` package
- **Pytorch**'s load and save methods by using their proprietary Torch Script as a `.pt` file. 
- **TensorFlow** saves models as `.pb` files; which is the protocol buffer files extension.
- **Keras** supports exporting in [hdf5](https://www.hdfgroup.org/solutions/hdf5) format. 
- There is also an alternative serialization package `dill` which generalizes pickle at the cost of performance.
- `ONNX` introduces a new paradigm: converting it to a set of operations that can be executed directly by the framework. This allows to decouple the model from your current python and virtual environment packages. This allows the model to be portable to to many different languages. `ONNX Runtime` is a performance-focused inference engine for ONNX models. ONNX Runtime was designed with a focus on performance and scalability in order to support heavy workloads in high-scale production scenarios.
***

## Guidelines
- Here are some guidelines for serialization.
  - Use [pickle](https://docs.python.org/3/library/pickle.html#module-pickle) to serialise objects with an importable hierarchy.
  - Use [joblib](https://joblib.readthedocs.io/en/latest/index.html) for objects which contain lots of data in numpy arrays.
  - Use [dill](https://pypi.org/project/dill/) when pickle or joblib won’t work, or when you have custom functions that need to be serialised as part of the model. In general, dill will provide the most flexibility in terms of getting the model serialised and should be considered the path of least resistance when it comes to serialising ML models for production.
***

## Available tutorials
- [How to save your Keras model.ipynb](https://github.com/kyaiooiayk/MLOps-Machine-Learning-Operations/blob/master/tutorials/Model_Serialisation/tutorials/GitHub_MD_rendering/How%20to%20save%20your%20Keras%20model.ipynb)
- [How to save your model with ONNX](https://github.com/kyaiooiayk/MLOps-Machine-Learning-Operations/blob/master/tutorials/Model_Serialisation/tutorials/GitHub_MD_rendering/How%20to%20save%20your%20model%20with%20ONNX.ipynb)
- [Model serialisation with dill](https://github.com/kyaiooiayk/MLOps-Machine-Learning-Operations/blob/master/tutorials/Model_Serialisation/tutorials/GitHub_MD_rendering/Model%20serialisation%20with%20dill.ipynb)
- [Save and load ML models](https://github.com/kyaiooiayk/MLOps-Machine-Learning-Operations/blob/master/tutorials/Model_Serialisation/tutorials/GitHub_MD_rendering/Save%20and%20load%20ML%20models.ipynb)
- [Model serialisation with pickle, joblib, skops](https://github.com/kyaiooiayk/MLOps-Machine-Learning-Operations/blob/master/tutorials/Model_Serialisation/tutorials/GitHub_MD_rendering/Model%20serialisation%20with%20pickle%2C%20joblib%2C%20skops.ipynb)
- [Exporting to ONNX](https://github.com/kyaiooiayk/PyTorch-Notes/blob/main/tutorials/GitHub_MD_rendering/Exporting%20to%20ONNX.ipynb)
- [PyTorch Lightning, ONNX Runtime](https://github.com/kyaiooiayk/PyTorch-Notes/blob/main/tutorials/GitHub_MD_rendering/PyTorch%20Lightning%2C%20ONNX%20Runtime.ipynb)
***

## References
- [Machine Learning Model Serialization](https://flynn.gg/blog/machine-learning-model-serialization/)
- [Serialization Wiki](https://en.wikipedia.org/wiki/Serialization)
- [How to easily deploy machine learning models using flask](https://towardsdatascience.com/how-to-easily-deploy-machine-learning-models-using-flask-b95af8fe34d4)
- [Three Levels of ML Software](https://ml-ops.org/content/three-levels-of-ml-software)
***
