# hello-world

Last night a DJ saved my life.

Edited with Atom.

*Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.*

from functions import *

def main():

    index = "ETF"
    series = "daily"
    transform = "diff"
    weekly = True

    # functions.simulate(index, series, weekly, transform, iterations=1)

    def plot_scatter(index, series):

        data = pd.read_csv("output/" + index + " " + series + "/coordinates-" + index + "-" + series + ".csv")

        # Draw plot
        fig, ax = plt.subplots()
        for name, group in data.groupby('category'):
            ax.plot(group.x, group.y, marker='o', linestyle='', ms=5, label=name)
        ax.legend(loc = 'right')

        box = ax.get_position()
        ax.set_position([box.x0, box.y0, box.width * 0.8, box.height])
        ax.legend(loc='center left', bbox_to_anchor=(1, 0.5))

        # df_xy.plot('x', 'y', kind='scatter', ax=ax, s=20)
        plt.axis('off')
        # plt.savefig("output/" + index + " " + series + "/img/scatter_" + index + "-" + series + ".png")
        plt.show()
        plt.close()

    plot_scatter(index, series)
    
    import xlwings as xw
import numpy as np
import pandas as pd

@xw.func
@xw.arg('x', np.array, ndim=2)
def matrix_mult(x, y):
    return x @ y

@xw.func
@xw.arg('x', pd.DataFrame, index=False, header=False)
def ds_to_csv(x):
    result = x.to_csv(r'C:\\Users\\Dmytro\\myproject\\result.csv', index=False, header=False)
    return "DONE"

    
