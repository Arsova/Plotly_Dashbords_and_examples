from plotly.offline import iplot, init_notebook_mode
import plotly.graph_objs as go
import plotly.io as pio
init_notebook_mode(connected=True)
import itertools
combinations=list(itertools.product(list(log_rep.columns), list(log_rep.columns))) # all combinations of two lists as a tuple
trans_tabels=[log_rep.T,df_step_2.T,df_step_3.T,df_step_4.T, df_step_5.T] # Transition matrices 

traces = [go.Scatter(
            x = np.arange(0, 5, 1),
            y=[df.loc[i] for df in trans_tabels],
            mode = 'markers+lines',
            name = str(i)
            ) for i in combinations]

updatemenus_ = list([
    dict(
        buttons = list([
            dict(
                args=['visible', True],
                label='show',
                method='restyle'
                ),
            dict(
                args=['visible', 'legendonly'],
                label='hide',
                method='restyle'
            )
        ]),
        direction = 'right',
        pad = {'r': 10, 't': 10},
        showactive = True,
        type = 'buttons',
        x = 0.5,
        xanchor = 'right',
        y = 1.1,
        yanchor = 'top'
    ),
])

layout = go.Layout(
    title = 'Transition probabilities within five steps for each transistion of people with repetitive behaviour'
)

layout['updatemenus'] = updatemenus_

fig = go.Figure(data=traces,layout=layout)
pyo.iplot(fig, filename='Transition_probabilities.html')
