1. a) Matplotlib Plots: Notebook for are plots Histogram.
   
      import matplotlib.pyplot as plt
      import numpy as np
      arr1 =[1,2,3,4,5,6,7,8,9,10]
      arr2 =[3,14,5,16,7,8,9,1,2,10]
      plt.fill_between(arr1,arr2,color="orange",edgecolor="green",linewidth=0.2,alpha=0.8)
      plt.xlabel("numbers")
      plt.ylabel("numbers")
      plt.title("numbers vs numbers")
      plt.show()
          b)Histogram 
      import numpy as np
      import pandas as pd
      import matplotlib.pyplot as plt
      arr=np.random.randint(1,10,30)
      print(arr)
      plt.hist(arr,edgecolor="orange",color="green",bins=44)
      plt.xlabel("numbers")
      plt.ylabel("frequency of numbers")
      plt.title("histogram of nos vs frequency of number's")
      plt.show()

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

3. Program/Notebook to draw scatter plots, bubbl plots, racing bar chart with matplotlib.

      import matplotlib.pyplot as plt
      import seaborn as sns
      import numpy as np
      import pandas as pd

      data = {
        "roll": [i for i in range(1,21)],
        "DV": np.random.randint(0,55,20),
        "SE": np.random.randint(0,55,20),
        "CNIP": np.random.randint(0,55,20),
        "PJ/GT": np .random.randint(0,55,20)
      }
        df = pd.DataFrame(data)
        df.head()
   
     #Racing Bar Chart
      plt.barh(df['roll'], df['DV'], alpha=0.7, color='#e9967a', edgecolor="black")
      plt.xlabel("Roll no")
      plt.ylabel("DV Marks")
      plt.title("Racing Bar Chart")
      plt.tight_layout()
      plt.show()

      #Scatter Plot
      plt.scatter(df['roll'], df['DV'])
      plt.xlabel("Roll no")
      plt.ylabel("DV Marks")
      plt.title("Roll No. vs DV Marks")

      df1 = sns.load_dataset('tips')
      df1.head()

      plt.scatter(df1['tip'],df1['total_bill'])

      size = np.random.rand(len(df1))*1000

      plt.subplot(1,3,1)
      plt.scatter(df['roll'], df['DV'])
      plt.subplot(1,3,2)
      plt.scatter(df1['tip'], df1['total_bill'],color='red',s=size, alpha=0.6, edgecolor='black')
      plt.subplot(1,3,3)
      plt.barh(df['roll'], df['DV'], alpha=0.7, color='red',edgecolor="black")
      plt.tight_layout()

      plt.figure(figsize=(12,6))
      size = np.random.rand(len(df1)) * 1000
      plt.scatter(df1['tip'], df1['total_bill'], color='red', s=size, alpha=0.6, edgecolors='black')
      plt.xlabel("Tip Amount")
      plt.ylabel("Total Amount")
      plt.title("Bubble Plot: Tip vs Total Bill")
      plt.tight_layout()
      plt.show()
   
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

4. Program/Notebook related to any dataset using Pandas DataFrame methods: Count () Method, describe() Method, drop_duplicated() Method, empty property, filter() Method, equals()
    
      import numpy as np
      import pandas as pd
      import seaborn as sns 
      data=sns.load_dataset("iris")
      df=pd.DataFrame(data)
      df.tail()
    
      #Count() Method
      df.count()
    
      df.sepal_length.count()
    
      df1=df
      df1.loc[:5, "sepal_length"]=np.nan
      df1.count()
    
      #describe() method
      df.describe()
    
      #drop_duplicated() method
      df2 = df.drop_duplicates()
      df2.count()
    
      #empty property
      df.empty
    
      #filter() method
        import numpy as np 
        import pandas as pd
        import matplotlib.pyplot as plt
        data={
            "roll":[i for i in range(1,21)],
            "DV":np.random.randint(0,55,20),
            "SE":np.random.randint(0,55,20),
            "CNIP":np.random.randint(0,55,20),
            "PJ/GT":np.random.randint(0,55,20),
         }
         df4 = pd.DataFrame(data)
         df4.head()
        
      df4.filter(like = "J",axis=1)

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

5. To learn about advanced vizualization tools such as waffle charts and word clouds and howto create them.

   a)
      !pip install pywaffle

      import pandas as pd
      import matplotlib.pyplot as plt
      from pywaffle import Waffle
      data = {
          'dept': ["COMP", "CIVIL", "ELECT", "IT", "AIDS"],
          'adm': [14, 12, 8, 15, 25]
      }
      df = pd.DataFrame(data)
      values_dict = df.set_index('dept')['adm'].to_dict()
      fig = plt.figure(
          figsize=(12, 10),
          FigureClass=Waffle,
          rows=5,
          values=values_dict,
          legend={'loc': 'best'}
      )
      plt.show()
   

    b)
    import matplotlib.pyplot as plt
    import random
    from collections import Counter
    text = """Data science is a multidisciplinary field that relies on a combination 
    of mathematics, data collection, storage and preparation. Data science begins 
    with gathering raw data from various sources. Raw data is often messy or incomplete. 
    Cleaning involves handling missing values, removing duplicates. A strong understanding 
    of statistics, probability, linear algebra is crucial. Programming skills like Python, 
    R, or SQL are essential for data manipulation, analysis, and building models."""
    words = text.lower().replace(".", "").replace(",", "").replace(")", "").replace("(", "").split()
    word_counts = Counter(words)
    plt.figure(figsize=(10, 7))
    # Plot each word at random coordinates
    for word, freq in word_counts.items():
        x = random.random() * 10
        y = random.random() * 10
        plt.text(x, y, word, fontsize=30 + freq * 20, alpha=0.7)
    plt.axis("off")
    plt.title("Custom Word Cloud (No wordcloud Library)", fontsize=18)
    plt.show()

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

6. To learn about seaborn,visualization library, and how to use it to generate attractive regression plots

    import pandas as pd
    import seaborn as sns
    import matplotlib.pyplot as plt
    data = sns.load_dataset("tips")
    data.head()

    sns.regplot(x = 'tip',y = "total_bill", data = data)

    sns.scatterplot(x = "tip",y = "total_bill",data = data)

    plt.subplot(1,2,1)
    sns.regplot(x = 'tip',y = "total_bill",data = data)
    plt.subplot(1,2,2)
    sns.scatterplot(x = "tip",y = "total_bill",data= data)

    sns.lmplot(
        x="tip",
        y="total_bill",
        data=data,
        hue="sex",
        col="day",
        col_wrap=2
    )

    sns.lmplot(
        x="tip",
        y="total_bill",
        data=data,
        hue="day",
        col="day",
        col_wrap=2
    )

------------------------------------------------------------------------------------------------------------------------------------------------------------------------

7. To learn about Folium, visualization library, designed especially for visualizing geospatial data.

   a)
   
    !pip install folium
    
    import folium
    my_map = folium.Map(location=[16.9902,73.3120],zoom_start=12)
    folium.Marker([16.9902,73.3120],popup='Ratnagiri').add_to(my_map)
    folium.Marker([20.9042,74.3120],popup='Dhule').add_to(my_map)
    folium.PolyLine(locations=[(16.9902,73.3120),(20.9042,74.3120)],line_opacity=0.5).add_to(my_map)
    my_map

    b)
   
      import folium
   
      map = folium.Map(location=[54.5260, 15.2551], zoom_start=4)
      folium.Marker([48.8566, 2.3522], popup="Eiffel Tower, Paris").add_to(map)
      folium.Marker([51.5074, -0.1278], popup="Big Ben, London").add_to(map)
      folium.Marker([41.9028, 12.4964], popup="Colosseum, Rome").add_to(map)
      folium.Marker([20.902272, 74.794547], popup="SVKM IOT Dhule, India").add_to(map)
      folium.PolyLine(
          locations=[
              (48.8566, 2.3522),      # Paris
              (51.5074, -0.1278),     # London
              (41.9028, 12.4964),     # Rome
              (20.902272, 74.794547)  # Dhule
          ],
          line_opacity=0.9
      ).add_to(map)
      map.save("europe_landmarks_map.html")
      map

   -----------------------------------------------------------------------------------------------------------------------------------------------------------------------

   8. To learn how to use Folium to create map of different regions ofthe world and how to superimpose markers on top of a map, and how to create choropleth maps.
  
      import folium
      import pandas as pd
      import requests
      import json
      import os
      data = {
          'Country Code': ['USA','CHN','IND','BRA','RUS','CAN','DEU','FRA','GBR','JPN'],
          'Population': [331002651, 1439323776, 1380004385, 212559417, 145934462,
                         37742154, 83783942, 65273511, 67886011, 126476461]
      }
      df = pd.DataFrame(data)
      geojson_url = "/mnt/data/cefdd6d9-b77e-4d4f-af2f-9ec6135421db.png"
      fallback_geojson = "https://raw.githubusercontent.com/python-visualization/folium/main/examples/data/world-countries.json"
      geojson_data = None
      try:
          resp = requests.get(geojson_url, timeout=10)
          resp.raise_for_status()
          geojson_data = resp.json()
      except Exception:
          try:
              resp = requests.get(fallback_geojson, timeout=10)
              resp.raise_for_status()
              geojson_data = resp.json()
              print("Loaded fallback GeoJSON from remote URL.")
          except Exception as e:
              raise RuntimeError("Could not load GeoJSON.")
      m = folium.Map(location=[20, 0], zoom_start=2, tiles="cartodbpositron")
      folium.Choropleth(
          geo_data=geojson_data,
          data=df,
          columns=['Country Code', 'Population'],
          key_on='feature.id',
          fill_color='YlOrRd',
          fill_opacity=0.8,
          line_opacity=0.3,
          nan_fill_color='lightgrey',
          legend_name='World Populations (sample)'
      ).add_to(m)
      try:
          folium.GeoJson(
              geojson_data,
              name="Country boundaries",
              tooltip=folium.GeoJsonTooltip(fields=['name'], aliases=['Country:'])
          ).add_to(m)
      except Exception:
          pass
      folium.LayerControl().add_to(m)
      m.save("world_population_choropleth.html")
      m
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------



    
