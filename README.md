# Ploting stars data to support star distribution suggested by Hertzsprung-Russel Diagram

### Data set and Tools
**Dataset:** I am using the data set of stars by Deepraj Baidya (kaggle.com/deepu1109) 
**Tools:** Kaggle.com, Python(pandas, numpy)

### Goals, processes and assumptions
**Goal:** the goal is to demonstrate how the data set of stars may support the Herztsprung-Russell model of star distribution by contructing a Hertzsprung-Russel Diagram.
**Constructing Hertzsprung-Russel Diagram:**
1. Assumption: 
Aside from Spectral class, Absolute magnitude and Star type, other columns are not neccessary, thus they will be omitted.
2. Constructing the diagram
Programming language: Python
Libraries: pandas, numpy, matplotlib
Steps:

    - Remap spectral class:
    Spectral class value are letters, thus the order for value in the scatterplot will be in the wrong order. To reorganize the values in the right order, the values are mapped to accending number from 0 to 6 and then added to the dataframe as a new column
            Python:
    "order_map = {'O': 0, 'B': 1, 'A': 2, 'F': 3, 'G': 4, 'K': 5, 'M': 6}
    df["mapped_spec"] = df["Spectral Class"].map(order_map)"
    -  Map color to star type:
    There are in total 6 star type correspondingh to a number from 0 to 5. The colors for each star type will be in this order:
        - 0: Brown Dwarf: brown
        - 1: Red Dwarf: red
        - 2: White Dwarf: white
        - 3: Main Sequence: orange
        - 4: Supergiant: yellow
        - 5: Hypergiant: royalblue

        Python:
        "star_type_color={0:'brown', 1:'red', 2:'white', 3:'orange', 4:'yellow', 5:'royalblue'}
        type_map_color=df['Star type'].map(star_type_color)"
    - Constructing the diagram:
    The diagram will be be constructed as a scatterplot using matplotlib.
    The x and y axis will be, in order, Spectral class and Absolute magnitude.
    Python:
        - Define the plot:
            "import matplotlib.pyplot as plt
            fig, ax = plt.subplots(figsize=(5, 7))"
        - Configuring the scatterplot:
            "plt.gca().invert_yaxis()
            ax.set_title("H-R DIAGRAM")
            ax.set_xlabel("Spectral Class")
            ax.set_ylabel("Absolute Magnitude")
            ax.set_xticks(range(0,7,1))
            ax.set_xticklabels(['O', 'B', 'A', 'F', 'G', 'K', 'M'])
            ax.scatter(df["mapped_spec"], df["Absolute magnitude(Mv)"], s=10, c=type_map_color)"

### Analysis
1. Hertzsprung-Russell Diagram:
Star distribution:
    - Giants(super and hyper): these are stars of immense mass with generally cooler temperature. They generally fall to the top right of the diagram (lower Absolute magnitude and closer to spectral class value M).
    - Main Sequence: these are stars of more average mass and temperature. They generally appear in the middle of the diagram (closer to 0 Absolute magnitude and closer to spectral class value F and G) .
    - White Dwarf: these are hot stars of small mass. They generally fall to the bottom left of the diagram (higher Absolute magnitude and closer to Spectral class value O).
    - Red Dwarf: these are cool and dim stars. They generally fall to the bottom right of the diagram (higher Absolute magnitude and closer to Spectral class value M).
    - Brown Dwarf: these are failed star, which are usually stellar objects that are not massive enough to sustain nuclear fusion. They can be seen as similar to Red Dwarf, but more cool and dim (higher Absolute magnitude and closer to Spectral class value M).
2. Plot comparison:
    - Giants(super and hyper): these stars are concentrated at the top in the scatterplot. This, for the most part, is consistent with their supposed distribution.
    - Main Sequence: these stars are concentrated in the middle of the scatterplot. They directly supports their supposed distribution,
    - White Dwarf: these stars are concentrated in the bottom left of the scatterplot. Similar to the Main Sequence stars, they are consistent with their supposed distribution
    - Red Dwarf: these stars are concentrated in the bottom right of the scatterplot. They, too, are consistent with their supposed distribution
    - Brown Dwarf: these stars are mostly distributed below the Red Dwarfs star in Absolute magnitude according to the scatterplot. Thus, this support their supposed distribution.
### Conclusion
Even though there are some exceptions regarding the giant stars and their supposed distribution, most of the data are consistent with the distribution suggested by the Hertzsprung-Russell Diagram.  