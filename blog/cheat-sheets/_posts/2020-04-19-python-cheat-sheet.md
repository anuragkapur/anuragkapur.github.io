---
layout: post
title:  "Python cheat sheet"
teaser: Python Cheat Sheet - Pandas, Numpy, Data Visualisation Using Matplotlib and Seaborn, Anaconda, Jupyter
date:   2020-04-19 00:00:00 +0000
categories: cheat-sheets
tags: cheat-sheets
permalink: /blog/python-cheat-sheet
---

<h3>Up-to-date version: <a href="https://github.com/anuragkapur/anuragkapur.github.io/blob/master/blog/cheat-sheets/jupyter/Python%20Cheat%20Sheet.ipynb" target="_blank">Python Cheat Sheet</a></h3>

  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p><h1>Table of Contents<span class="tocSkip"></span></h1></p>
<div class="toc"><ul class="toc-item"><li><span><a href="#Numpy" data-toc-modified-id="Numpy-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>Numpy</a></span><ul class="toc-item"><li><span><a href="#Create-Numpy-Array-from-Python-List" data-toc-modified-id="Create-Numpy-Array-from-Python-List-1.1"><span class="toc-item-num">1.1&nbsp;&nbsp;</span>Create Numpy Array from Python List</a></span></li><li><span><a href="#Create-Numpy-Array-from-Built-in-Functions" data-toc-modified-id="Create-Numpy-Array-from-Built-in-Functions-1.2"><span class="toc-item-num">1.2&nbsp;&nbsp;</span>Create Numpy Array from Built-in Functions</a></span></li><li><span><a href="#Accessing,-Deleting-and-Inserting-Elements-into-NDArrays" data-toc-modified-id="Accessing,-Deleting-and-Inserting-Elements-into-NDArrays-1.3"><span class="toc-item-num">1.3&nbsp;&nbsp;</span>Accessing, Deleting and Inserting Elements into NDArrays</a></span></li><li><span><a href="#Slicing-NDArrays" data-toc-modified-id="Slicing-NDArrays-1.4"><span class="toc-item-num">1.4&nbsp;&nbsp;</span>Slicing NDArrays</a></span></li><li><span><a href="#Boolean-Indexing" data-toc-modified-id="Boolean-Indexing-1.5"><span class="toc-item-num">1.5&nbsp;&nbsp;</span>Boolean Indexing</a></span></li><li><span><a href="#Set-Operations" data-toc-modified-id="Set-Operations-1.6"><span class="toc-item-num">1.6&nbsp;&nbsp;</span>Set Operations</a></span></li><li><span><a href="#Sorting" data-toc-modified-id="Sorting-1.7"><span class="toc-item-num">1.7&nbsp;&nbsp;</span>Sorting</a></span></li></ul></li><li><span><a href="#Pandas" data-toc-modified-id="Pandas-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>Pandas</a></span><ul class="toc-item"><li><span><a href="#Pandas-Series" data-toc-modified-id="Pandas-Series-2.1"><span class="toc-item-num">2.1&nbsp;&nbsp;</span>Pandas Series</a></span><ul class="toc-item"><li><span><a href="#Create" data-toc-modified-id="Create-2.1.1"><span class="toc-item-num">2.1.1&nbsp;&nbsp;</span>Create</a></span></li><li><span><a href="#Attributes" data-toc-modified-id="Attributes-2.1.2"><span class="toc-item-num">2.1.2&nbsp;&nbsp;</span>Attributes</a></span></li><li><span><a href="#Accessing-Data" data-toc-modified-id="Accessing-Data-2.1.3"><span class="toc-item-num">2.1.3&nbsp;&nbsp;</span>Accessing Data</a></span></li><li><span><a href="#Modify-Series" data-toc-modified-id="Modify-Series-2.1.4"><span class="toc-item-num">2.1.4&nbsp;&nbsp;</span>Modify Series</a></span></li><li><span><a href="#Arithmetic-Operations" data-toc-modified-id="Arithmetic-Operations-2.1.5"><span class="toc-item-num">2.1.5&nbsp;&nbsp;</span>Arithmetic Operations</a></span></li></ul></li><li><span><a href="#Pandas-DataFrames" data-toc-modified-id="Pandas-DataFrames-2.2"><span class="toc-item-num">2.2&nbsp;&nbsp;</span>Pandas DataFrames</a></span><ul class="toc-item"><li><span><a href="#Create" data-toc-modified-id="Create-2.2.1"><span class="toc-item-num">2.2.1&nbsp;&nbsp;</span>Create</a></span></li><li><span><a href="#Attributes" data-toc-modified-id="Attributes-2.2.2"><span class="toc-item-num">2.2.2&nbsp;&nbsp;</span>Attributes</a></span></li><li><span><a href="#Accessing-Data" data-toc-modified-id="Accessing-Data-2.2.3"><span class="toc-item-num">2.2.3&nbsp;&nbsp;</span>Accessing Data</a></span><ul class="toc-item"><li><span><a href="#Access-column(s)-by-label" data-toc-modified-id="Access-column(s)-by-label-2.2.3.1"><span class="toc-item-num">2.2.3.1&nbsp;&nbsp;</span>Access column(s) by label</a></span></li><li><span><a href="#Access-column(s)-by-index" data-toc-modified-id="Access-column(s)-by-index-2.2.3.2"><span class="toc-item-num">2.2.3.2&nbsp;&nbsp;</span>Access column(s) by index</a></span></li><li><span><a href="#Access-row(s)-by-label" data-toc-modified-id="Access-row(s)-by-label-2.2.3.3"><span class="toc-item-num">2.2.3.3&nbsp;&nbsp;</span>Access row(s) by label</a></span></li><li><span><a href="#Access-row(s)-by-index" data-toc-modified-id="Access-row(s)-by-index-2.2.3.4"><span class="toc-item-num">2.2.3.4&nbsp;&nbsp;</span>Access row(s) by index</a></span></li><li><span><a href="#Get-N-rows-from-a-DF" data-toc-modified-id="Get-N-rows-from-a-DF-2.2.3.5"><span class="toc-item-num">2.2.3.5&nbsp;&nbsp;</span>Get N rows from a DF</a></span></li><li><span><a href="#Get-N-random-rows-from-a-DF" data-toc-modified-id="Get-N-random-rows-from-a-DF-2.2.3.6"><span class="toc-item-num">2.2.3.6&nbsp;&nbsp;</span>Get N random rows from a DF</a></span></li><li><span><a href="#Access-element-by-row-and-column-label" data-toc-modified-id="Access-element-by-row-and-column-label-2.2.3.7"><span class="toc-item-num">2.2.3.7&nbsp;&nbsp;</span>Access element by row and column label</a></span></li><li><span><a href="#Get-all-rows-where-column-value-satisfies-condition" data-toc-modified-id="Get-all-rows-where-column-value-satisfies-condition-2.2.3.8"><span class="toc-item-num">2.2.3.8&nbsp;&nbsp;</span>Get all rows where column value satisfies condition</a></span></li></ul></li><li><span><a href="#Modify-DF" data-toc-modified-id="Modify-DF-2.2.4"><span class="toc-item-num">2.2.4&nbsp;&nbsp;</span>Modify DF</a></span><ul class="toc-item"><li><span><a href="#Add-column" data-toc-modified-id="Add-column-2.2.4.1"><span class="toc-item-num">2.2.4.1&nbsp;&nbsp;</span>Add column</a></span></li><li><span><a href="#Append-columns-from-a-DF-to-another-DF" data-toc-modified-id="Append-columns-from-a-DF-to-another-DF-2.2.4.2"><span class="toc-item-num">2.2.4.2&nbsp;&nbsp;</span>Append columns from a DF to another DF</a></span></li><li><span><a href="#Insert-column-at-index" data-toc-modified-id="Insert-column-at-index-2.2.4.3"><span class="toc-item-num">2.2.4.3&nbsp;&nbsp;</span>Insert column at index</a></span></li><li><span><a href="#Add-column-using-sum-of-previous-columns-values" data-toc-modified-id="Add-column-using-sum-of-previous-columns-values-2.2.4.4"><span class="toc-item-num">2.2.4.4&nbsp;&nbsp;</span>Add column using sum of previous columns values</a></span></li><li><span><a href="#Add-rows" data-toc-modified-id="Add-rows-2.2.4.5"><span class="toc-item-num">2.2.4.5&nbsp;&nbsp;</span>Add rows</a></span></li><li><span><a href="#Delete-column" data-toc-modified-id="Delete-column-2.2.4.6"><span class="toc-item-num">2.2.4.6&nbsp;&nbsp;</span>Delete column</a></span></li><li><span><a href="#Delete-multiple-columns" data-toc-modified-id="Delete-multiple-columns-2.2.4.7"><span class="toc-item-num">2.2.4.7&nbsp;&nbsp;</span>Delete multiple columns</a></span></li><li><span><a href="#Delete-multiple-rows" data-toc-modified-id="Delete-multiple-rows-2.2.4.8"><span class="toc-item-num">2.2.4.8&nbsp;&nbsp;</span>Delete multiple rows</a></span></li><li><span><a href="#Transform-values-of-selected-columns" data-toc-modified-id="Transform-values-of-selected-columns-2.2.4.9"><span class="toc-item-num">2.2.4.9&nbsp;&nbsp;</span>Transform values of selected columns</a></span></li></ul></li><li><span><a href="#Dealing-with-NaN" data-toc-modified-id="Dealing-with-NaN-2.2.5"><span class="toc-item-num">2.2.5&nbsp;&nbsp;</span>Dealing with NaN</a></span></li><li><span><a href="#Statistical-Analysis" data-toc-modified-id="Statistical-Analysis-2.2.6"><span class="toc-item-num">2.2.6&nbsp;&nbsp;</span>Statistical Analysis</a></span></li></ul></li></ul></li><li><span><a href="#Data-Visualisation" data-toc-modified-id="Data-Visualisation-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>Data Visualisation</a></span><ul class="toc-item"><li><span><a href="#Univariate-Data" data-toc-modified-id="Univariate-Data-3.1"><span class="toc-item-num">3.1&nbsp;&nbsp;</span>Univariate Data</a></span><ul class="toc-item"><li><span><a href="#Categorical-data-frequency/count-as-bar-chart" data-toc-modified-id="Categorical-data-frequency/count-as-bar-chart-3.1.1"><span class="toc-item-num">3.1.1&nbsp;&nbsp;</span>Categorical data frequency/count as bar chart</a></span></li><li><span><a href="#Categorical-data-relative-frequency-as-bar-chart" data-toc-modified-id="Categorical-data-relative-frequency-as-bar-chart-3.1.2"><span class="toc-item-num">3.1.2&nbsp;&nbsp;</span>Categorical data relative frequency as bar chart</a></span></li><li><span><a href="#Using-Barplot-to-visualise-processed-data-(not-already-stored-as-a-column-value)" data-toc-modified-id="Using-Barplot-to-visualise-processed-data-(not-already-stored-as-a-column-value)-3.1.3"><span class="toc-item-num">3.1.3&nbsp;&nbsp;</span>Using Barplot to visualise processed data (not already stored as a column value)</a></span></li><li><span><a href="#Numerical-data-histograms" data-toc-modified-id="Numerical-data-histograms-3.1.4"><span class="toc-item-num">3.1.4&nbsp;&nbsp;</span>Numerical data histograms</a></span></li></ul></li><li><span><a href="#Subplots-(Stack-Plots-Horizontally)" data-toc-modified-id="Subplots-(Stack-Plots-Horizontally)-3.2"><span class="toc-item-num">3.2&nbsp;&nbsp;</span>Subplots (Stack Plots Horizontally)</a></span></li><li><span><a href="#Plot-Subset-of-Data-(Axis-Range-Limits)" data-toc-modified-id="Plot-Subset-of-Data-(Axis-Range-Limits)-3.3"><span class="toc-item-num">3.3&nbsp;&nbsp;</span>Plot Subset of Data (Axis Range Limits)</a></span></li><li><span><a href="#Axis-Transformations-(Log-Scale)" data-toc-modified-id="Axis-Transformations-(Log-Scale)-3.4"><span class="toc-item-num">3.4&nbsp;&nbsp;</span>Axis Transformations (Log Scale)</a></span></li><li><span><a href="#Bivariate-Data" data-toc-modified-id="Bivariate-Data-3.5"><span class="toc-item-num">3.5&nbsp;&nbsp;</span>Bivariate Data</a></span><ul class="toc-item"><li><span><a href="#Pairwise-Relationship-Between-Numerical-Columns" data-toc-modified-id="Pairwise-Relationship-Between-Numerical-Columns-3.5.1"><span class="toc-item-num">3.5.1&nbsp;&nbsp;</span>Pairwise Relationship Between Numerical Columns</a></span></li><li><span><a href="#Categorical-daya-grouped-by-another-label" data-toc-modified-id="Categorical-daya-grouped-by-another-label-3.5.2"><span class="toc-item-num">3.5.2&nbsp;&nbsp;</span>Categorical daya grouped-by another label</a></span></li></ul></li></ul></li><li><span><a href="#Anaconda" data-toc-modified-id="Anaconda-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>Anaconda</a></span><ul class="toc-item"><li><span><a href="#List-envs" data-toc-modified-id="List-envs-4.1"><span class="toc-item-num">4.1&nbsp;&nbsp;</span>List envs</a></span></li><li><span><a href="#Activate-env" data-toc-modified-id="Activate-env-4.2"><span class="toc-item-num">4.2&nbsp;&nbsp;</span>Activate env</a></span></li><li><span><a href="#Update-all-packages" data-toc-modified-id="Update-all-packages-4.3"><span class="toc-item-num">4.3&nbsp;&nbsp;</span>Update all packages</a></span></li><li><span><a href="#Install-package" data-toc-modified-id="Install-package-4.4"><span class="toc-item-num">4.4&nbsp;&nbsp;</span>Install package</a></span></li><li><span><a href="#Remove-package" data-toc-modified-id="Remove-package-4.5"><span class="toc-item-num">4.5&nbsp;&nbsp;</span>Remove package</a></span></li><li><span><a href="#Search-package" data-toc-modified-id="Search-package-4.6"><span class="toc-item-num">4.6&nbsp;&nbsp;</span>Search package</a></span></li><li><span><a href="#List-packages" data-toc-modified-id="List-packages-4.7"><span class="toc-item-num">4.7&nbsp;&nbsp;</span>List packages</a></span></li></ul></li><li><span><a href="#Jupyter" data-toc-modified-id="Jupyter-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>Jupyter</a></span><ul class="toc-item"><li><span><a href="#Convert-notebook-to-html" data-toc-modified-id="Convert-notebook-to-html-5.1"><span class="toc-item-num">5.1&nbsp;&nbsp;</span>Convert notebook to html</a></span></li><li><span><a href="#Add-TOC" data-toc-modified-id="Add-TOC-5.2"><span class="toc-item-num">5.2&nbsp;&nbsp;</span>Add TOC</a></span></li></ul></li></ul></div>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Numpy">Numpy<a class="anchor-link" href="#Numpy">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Create-Numpy-Array-from-Python-List">Create Numpy Array from Python List<a class="anchor-link" href="#Create-Numpy-Array-from-Python-List">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="nb">type</span><span class="p">(</span><span class="n">x</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">dtype</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">size</span><span class="p">)</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">],</span> <span class="p">[</span><span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">6</span><span class="p">],</span> <span class="p">[</span><span class="mi">7</span><span class="p">,</span> <span class="mi">8</span><span class="p">,</span> <span class="mi">9</span><span class="p">],</span> <span class="p">[</span><span class="mi">10</span><span class="p">,</span> <span class="mi">11</span><span class="p">,</span> <span class="mi">12</span><span class="p">]])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="nb">type</span><span class="p">(</span><span class="n">x</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">dtype</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">size</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[1 2 3 4 5]
&lt;class &#39;numpy.ndarray&#39;&gt;
int64
(5,)
5
[[ 1  2  3]
 [ 4  5  6]
 [ 7  8  9]
 [10 11 12]]
&lt;class &#39;numpy.ndarray&#39;&gt;
int64
(4, 3)
12
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Create-Numpy-Array-from-Built-in-Functions">Create Numpy Array from Built-in Functions<a class="anchor-link" href="#Create-Numpy-Array-from-Built-in-Functions">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[32]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">dtype</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]]
float64
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[33]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">ones</span><span class="p">((</span><span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">),</span> <span class="n">dtype</span><span class="o">=</span><span class="nb">int</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">dtype</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[1 1 1 1]
 [1 1 1 1]
 [1 1 1 1]]
int64
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[34]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">full</span><span class="p">((</span><span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">),</span> <span class="mi">5</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[5 5 5 5]
 [5 5 5 5]
 [5 5 5 5]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[35]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">eye</span><span class="p">(</span><span class="mi">5</span><span class="p">,</span> <span class="n">dtype</span><span class="o">=</span><span class="nb">int</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[1 0 0 0 0]
 [0 1 0 0 0]
 [0 0 1 0 0]
 [0 0 0 1 0]
 [0 0 0 0 1]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[36]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">diag</span><span class="p">([</span><span class="mi">10</span><span class="p">,</span> <span class="mi">20</span><span class="p">,</span> <span class="mi">30</span><span class="p">,</span> <span class="mi">40</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[10  0  0  0]
 [ 0 20  0  0]
 [ 0  0 30  0]
 [ 0  0  0 40]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[37]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">4</span><span class="p">,</span> <span class="mi">10</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[4 5 6 7 8 9]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[41]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">20</span><span class="p">,</span> <span class="mi">3</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[ 1  4  7 10 13 16 19]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[42]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">linspace</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">20</span><span class="p">,</span> <span class="mi">3</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[ 1.  10.5 20. ]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[44]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">20</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="p">(</span><span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">20</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[ 0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19]
[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]]
[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[48]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Defaults to range [0, 1)</span>
<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">random</span><span class="o">.</span><span class="n">random</span><span class="p">((</span><span class="mi">3</span><span class="p">,</span> <span class="mi">3</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">random</span><span class="o">.</span><span class="n">randint</span><span class="p">(</span><span class="mi">4</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="p">(</span><span class="mi">3</span><span class="p">,</span> <span class="mi">3</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[0.22087021 0.53229498 0.58663932]
 [0.21300366 0.86993844 0.56059265]
 [0.86554777 0.38157681 0.78204005]]
[[7 5 9]
 [7 4 7]
 [9 9 7]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[56]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># mean = 0, std = 0.1</span>
<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">random</span><span class="o">.</span><span class="n">normal</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mf">0.1</span><span class="p">,</span> <span class="p">(</span><span class="mi">5</span><span class="p">,</span> <span class="mi">5</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">mean</span><span class="p">())</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="o">.</span><span class="n">std</span><span class="p">())</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[ 0.0122765  -0.12708003  0.11426993 -0.04997364 -0.02526457]
 [-0.04439879 -0.12928117 -0.07242298  0.060275    0.06836317]
 [-0.02163878  0.15118322 -0.09682757 -0.04438684  0.11186937]
 [ 0.03933767 -0.08154594  0.00507315 -0.05448884  0.06592437]
 [ 0.06140125 -0.0002377  -0.07852702 -0.02126833  0.17878217]]
0.0008565443649252224
0.08241037010812466
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Accessing,-Deleting-and-Inserting-Elements-into-NDArrays">Accessing, Deleting and Inserting Elements into NDArrays<a class="anchor-link" href="#Accessing,-Deleting-and-Inserting-Elements-into-NDArrays">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[59]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">])</span>

<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">[</span><span class="mi">0</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">[</span><span class="mi">2</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">[</span><span class="o">-</span><span class="mi">1</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">[</span><span class="o">-</span><span class="mi">3</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>1
3
5
3
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[105]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Get  diagonal of a 2d array</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">25</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">5</span><span class="p">,</span> <span class="mi">5</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">diag</span><span class="p">(</span><span class="n">x</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">diag</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">k</span><span class="o">=</span><span class="mi">1</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">diag</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">k</span><span class="o">=-</span><span class="mi">2</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]
 [20 21 22 23 24]]
[ 0  6 12 18 24]
[ 1  7 13 19]
[10 16 22]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[106]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Get unique elements of an array</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">5</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">unique</span><span class="p">(</span><span class="n">x</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[1 2 3 4 5]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[62]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">10</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">3</span><span class="p">,</span> <span class="mi">3</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">0</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">0</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">[</span><span class="mi">2</span><span class="p">,</span> <span class="mi">1</span><span class="p">])</span>

<span class="c1">## Modify element</span>
<span class="n">x</span><span class="p">[</span><span class="mi">2</span><span class="p">,</span> <span class="mi">2</span><span class="p">]</span> <span class="o">=</span> <span class="o">-</span><span class="mi">9</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[1 2 3]
 [4 5 6]
 [7 8 9]]
1
4
8
[[ 1  2  3]
 [ 4  5  6]
 [ 7  8 -9]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[67]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Delete Rows by Index</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">9</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">3</span><span class="p">,</span> <span class="mi">3</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">delete</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">2</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[0 1 2]
 [3 4 5]
 [6 7 8]]
[[3 4 5]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[70]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Delete Columns by Index</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">9</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">3</span><span class="p">,</span> <span class="mi">3</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">delete</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">2</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[0 1 2]
 [3 4 5]
 [6 7 8]]
[[1]
 [4]
 [7]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[72]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Append Row</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">9</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">3</span><span class="p">,</span> <span class="mi">3</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="p">[[</span><span class="mi">9</span><span class="p">,</span> <span class="mi">10</span><span class="p">,</span> <span class="mi">11</span><span class="p">]],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[0 1 2]
 [3 4 5]
 [6 7 8]]
[[ 0  1  2]
 [ 3  4  5]
 [ 6  7  8]
 [ 9 10 11]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[74]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Append Column</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">9</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">3</span><span class="p">,</span> <span class="mi">3</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="p">[[</span><span class="mi">9</span><span class="p">],</span> <span class="p">[</span><span class="mi">10</span><span class="p">],</span> <span class="p">[</span><span class="mi">11</span><span class="p">]],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[0 1 2]
 [3 4 5]
 [6 7 8]]
[[ 0  1  2  9]
 [ 3  4  5 10]
 [ 6  7  8 11]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[77]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Insert Elements - 1D / Rank 1 Arrays</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">6</span><span class="p">,</span> <span class="mi">7</span><span class="p">,</span> <span class="mi">8</span><span class="p">,</span> <span class="mi">9</span><span class="p">,</span> <span class="mi">10</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">insert</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="p">[</span><span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">]))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[ 1  2  5  6  7  8  9 10]
[ 1  2  3  4  5  6  7  8  9 10]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[79]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Insert Row at Specified Index - 2D Array</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">],</span> <span class="p">[</span><span class="mi">7</span><span class="p">,</span> <span class="mi">8</span><span class="p">,</span> <span class="mi">9</span><span class="p">]])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">insert</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="mi">1</span><span class="p">,</span> <span class="p">[</span><span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">,</span> <span class="mi">6</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[1 2 3]
 [7 8 9]]
[[1 2 3]
 [4 5 6]
 [7 8 9]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[83]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">],</span> <span class="p">[</span><span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">]])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">insert</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="p">[</span><span class="mi">3</span><span class="p">,</span> <span class="mi">6</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">insert</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">9</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[1 2]
 [4 5]]
[[1 2 3]
 [4 5 6]]
[[1 2 9]
 [4 5 9]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[90]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Stack 2 Arrays - Vertically</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">])</span>
<span class="n">y</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([[</span><span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">],</span> <span class="p">[</span><span class="mi">5</span><span class="p">,</span> <span class="mi">6</span><span class="p">]])</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;x=</span><span class="se">\n</span><span class="si">{</span><span class="n">x</span><span class="si">}</span><span class="s2">&quot;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;y=</span><span class="se">\n</span><span class="si">{</span><span class="n">y</span><span class="si">}</span><span class="s2">&quot;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;vstack=</span><span class="se">\n</span><span class="s2"> </span><span class="si">{</span><span class="n">np</span><span class="o">.</span><span class="n">vstack</span><span class="p">((</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">))</span><span class="si">}</span><span class="s2">&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>x=
[1 2]
y=
[[3 4]
 [5 6]]
vstack=
 [[1 2]
 [3 4]
 [5 6]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[93]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Stack 2 Arrays - Horizontally</span>

<span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([[</span><span class="mi">3</span><span class="p">],</span> <span class="p">[</span><span class="mi">6</span><span class="p">]])</span>
<span class="n">y</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">],</span> <span class="p">[</span><span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">]])</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;x=</span><span class="se">\n</span><span class="si">{</span><span class="n">x</span><span class="si">}</span><span class="s2">&quot;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;y=</span><span class="se">\n</span><span class="si">{</span><span class="n">y</span><span class="si">}</span><span class="s2">&quot;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;hstack=</span><span class="se">\n</span><span class="s2"> </span><span class="si">{</span><span class="n">np</span><span class="o">.</span><span class="n">hstack</span><span class="p">((</span><span class="n">y</span><span class="p">,</span> <span class="n">x</span><span class="p">))</span><span class="si">}</span><span class="s2">&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>x=
[[3]
 [6]]
y=
[[1 2]
 [4 5]]
hstack=
 [[1 2 3]
 [4 5 6]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Slicing-NDArrays">Slicing NDArrays<a class="anchor-link" href="#Slicing-NDArrays">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Slicing only creates new "views" on the original array, not new copies of the sliced array. To create a copy, use the <code>copy()</code> method.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[99]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">21</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">[</span><span class="mi">0</span><span class="p">:</span><span class="mi">2</span><span class="p">,</span> <span class="mi">0</span><span class="p">:</span><span class="mi">2</span><span class="p">])</span>

<span class="c1">## Notice the subtle difference between the followig</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">[:,</span> <span class="mi">0</span><span class="p">:</span><span class="mi">1</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">[:,</span> <span class="mi">0</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[ 1  2  3  4  5]
 [ 6  7  8  9 10]
 [11 12 13 14 15]
 [16 17 18 19 20]]
[[1 2]
 [6 7]]
[[ 1]
 [ 6]
 [11]
 [16]]
[ 1  6 11 16]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Boolean-Indexing">Boolean Indexing<a class="anchor-link" href="#Boolean-Indexing">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[109]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">25</span><span class="p">)</span><span class="o">.</span><span class="n">reshape</span><span class="p">(</span><span class="mi">5</span><span class="p">,</span> <span class="mi">5</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>

<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">[(</span><span class="n">x</span> <span class="o">&gt;</span> <span class="mi">10</span><span class="p">)</span> <span class="o">&amp;</span> <span class="p">(</span><span class="n">x</span> <span class="o">&lt;</span> <span class="mi">17</span><span class="p">)])</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[ 0  1  2  3  4]
 [ 5  6  7  8  9]
 [10 11 12 13 14]
 [15 16 17 18 19]
 [20 21 22 23 24]]
[11 12 13 14 15 16]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Set-Operations">Set Operations<a class="anchor-link" href="#Set-Operations">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[110]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">])</span>
<span class="n">y</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">array</span><span class="p">([</span><span class="mi">6</span><span class="p">,</span> <span class="mi">8</span><span class="p">,</span> <span class="mi">3</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">9</span><span class="p">])</span>

<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">intersect1d</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">setdiff1d</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">np</span><span class="o">.</span><span class="n">union1d</span><span class="p">(</span><span class="n">x</span><span class="p">,</span> <span class="n">y</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[2 3]
[1 4 5]
[1 2 3 4 5 6 8 9]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Sorting">Sorting<a class="anchor-link" href="#Sorting">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[119]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">x</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">random</span><span class="o">.</span><span class="n">randint</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">11</span><span class="p">,</span> <span class="n">size</span><span class="o">=</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="p">))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">x</span><span class="p">)</span>

<span class="c1">## Out-of-place sorting</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;oop sorted= </span><span class="se">\n</span><span class="s2"> </span><span class="si">{</span><span class="n">np</span><span class="o">.</span><span class="n">sort</span><span class="p">(</span><span class="n">x</span><span class="p">)</span><span class="si">}</span><span class="s2">&quot;</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;original= </span><span class="se">\n</span><span class="s2"> </span><span class="si">{</span><span class="n">x</span><span class="si">}</span><span class="s2">&quot;</span><span class="p">)</span>

<span class="c1">## In-place sorting</span>
<span class="n">x</span><span class="o">.</span><span class="n">sort</span><span class="p">()</span>
<span class="nb">print</span><span class="p">(</span><span class="sa">f</span><span class="s2">&quot;ip sorted= </span><span class="se">\n</span><span class="s2"> </span><span class="si">{</span><span class="n">x</span><span class="si">}</span><span class="s2">&quot;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[9 1 8 9 6 1 7 6 2 8]
oop sorted= 
 [1 1 2 6 6 7 8 8 9 9]
original= 
 [9 1 8 9 6 1 7 6 2 8]
ip sorted= 
 [1 1 2 6 6 7 8 8 9 9]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Pandas">Pandas<a class="anchor-link" href="#Pandas">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[121]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Pandas-Series">Pandas Series<a class="anchor-link" href="#Pandas-Series">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Create">Create<a class="anchor-link" href="#Create">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[128]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">### With default integer indices</span>
<span class="n">groceries</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span><span class="o">=</span><span class="p">[</span><span class="mi">30</span><span class="p">,</span> <span class="mi">6</span><span class="p">,</span> <span class="s1">&#39;Foo&#39;</span><span class="p">,</span> <span class="s1">&#39;Bar&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="p">)</span>

<span class="c1">### With custom indices</span>
<span class="n">groceries</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span><span class="o">=</span><span class="p">[</span><span class="mi">30</span><span class="p">,</span> <span class="mi">6</span><span class="p">,</span> <span class="s1">&#39;Yes&#39;</span><span class="p">,</span> <span class="s1">&#39;No&#39;</span><span class="p">],</span> <span class="n">index</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;egg&#39;</span><span class="p">,</span> <span class="s1">&#39;apples&#39;</span><span class="p">,</span> <span class="s1">&#39;milk&#39;</span><span class="p">,</span> <span class="s1">&#39;bread&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>0     30
1      6
2    Foo
3    Bar
dtype: object
egg        30
apples      6
milk      Yes
bread      No
dtype: object
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Attributes">Attributes<a class="anchor-link" href="#Attributes">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[130]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="o">.</span><span class="n">shape</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="o">.</span><span class="n">ndim</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="o">.</span><span class="n">size</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="o">.</span><span class="n">index</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="o">.</span><span class="n">values</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;bananas&#39;</span> <span class="ow">in</span> <span class="n">groceries</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;apples&#39;</span> <span class="ow">in</span> <span class="n">groceries</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>(4,)
1
4
Index([&#39;egg&#39;, &#39;apples&#39;, &#39;milk&#39;, &#39;bread&#39;], dtype=&#39;object&#39;)
[30 6 &#39;Yes&#39; &#39;No&#39;]
False
True
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Accessing-Data">Accessing Data<a class="anchor-link" href="#Accessing-Data">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[144]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">groceries</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span><span class="o">=</span><span class="p">[</span><span class="mi">30</span><span class="p">,</span> <span class="mi">6</span><span class="p">,</span> <span class="s1">&#39;Yes&#39;</span><span class="p">,</span> <span class="s1">&#39;No&#39;</span><span class="p">],</span> <span class="n">index</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;egg&#39;</span><span class="p">,</span> <span class="s1">&#39;apples&#39;</span><span class="p">,</span> <span class="s1">&#39;milk&#39;</span><span class="p">,</span> <span class="s1">&#39;bread&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="p">[</span><span class="s1">&#39;egg&#39;</span><span class="p">])</span>

<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;====</span><span class="se">\n</span><span class="s1">&#39;</span><span class="p">)</span>

<span class="c1">## By labels</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="p">[[</span><span class="s1">&#39;egg&#39;</span><span class="p">,</span> <span class="s1">&#39;apples&#39;</span><span class="p">]])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;egg&#39;</span><span class="p">,</span> <span class="s1">&#39;apples&#39;</span><span class="p">]])</span>
<span class="nb">print</span><span class="p">(</span><span class="s1">&#39;====</span><span class="se">\n</span><span class="s1">&#39;</span><span class="p">)</span>

<span class="c1">## By index</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="p">[[</span><span class="mi">0</span><span class="p">,</span> <span class="o">-</span><span class="mi">1</span><span class="p">]])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="o">.</span><span class="n">iloc</span><span class="p">[[</span><span class="mi">0</span><span class="p">,</span> <span class="o">-</span><span class="mi">1</span><span class="p">]])</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>30
====

egg       30
apples     6
dtype: object
egg       30
apples     6
dtype: object
====

egg      30
bread    No
dtype: object
egg      30
bread    No
dtype: object
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Modify-Series">Modify Series<a class="anchor-link" href="#Modify-Series">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[145]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Change Element Values</span>
<span class="n">groceries</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span><span class="o">=</span><span class="p">[</span><span class="mi">30</span><span class="p">,</span> <span class="mi">6</span><span class="p">,</span> <span class="s1">&#39;Yes&#39;</span><span class="p">,</span> <span class="s1">&#39;No&#39;</span><span class="p">],</span> <span class="n">index</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;egg&#39;</span><span class="p">,</span> <span class="s1">&#39;apples&#39;</span><span class="p">,</span> <span class="s1">&#39;milk&#39;</span><span class="p">,</span> <span class="s1">&#39;bread&#39;</span><span class="p">])</span>
<span class="n">groceries</span><span class="p">[[</span><span class="s1">&#39;egg&#39;</span><span class="p">]]</span> <span class="o">=</span> <span class="mi">31</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>egg        31
apples      6
milk      Yes
bread      No
dtype: object
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[153]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Drop Elements - Out-of-Place</span>
<span class="n">groceries</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span><span class="o">=</span><span class="p">[</span><span class="mi">30</span><span class="p">,</span> <span class="mi">6</span><span class="p">,</span> <span class="s1">&#39;Yes&#39;</span><span class="p">,</span> <span class="s1">&#39;No&#39;</span><span class="p">],</span> <span class="n">index</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;egg&#39;</span><span class="p">,</span> <span class="s1">&#39;apples&#39;</span><span class="p">,</span> <span class="s1">&#39;milk&#39;</span><span class="p">,</span> <span class="s1">&#39;bread&#39;</span><span class="p">])</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;apples&#39;</span><span class="p">]))</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>egg       30
milk     Yes
bread     No
dtype: object
egg        30
apples      6
milk      Yes
bread      No
dtype: object
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[155]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Drop Elements - In-Place</span>
<span class="n">groceries</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span><span class="o">=</span><span class="p">[</span><span class="mi">30</span><span class="p">,</span> <span class="mi">6</span><span class="p">,</span> <span class="s1">&#39;Yes&#39;</span><span class="p">,</span> <span class="s1">&#39;No&#39;</span><span class="p">],</span> <span class="n">index</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;egg&#39;</span><span class="p">,</span> <span class="s1">&#39;apples&#39;</span><span class="p">,</span> <span class="s1">&#39;milk&#39;</span><span class="p">,</span> <span class="s1">&#39;bread&#39;</span><span class="p">])</span>
<span class="n">groceries</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;apples&#39;</span><span class="p">],</span> <span class="n">inplace</span><span class="o">=</span><span class="kc">True</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">groceries</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>egg       30
milk     Yes
bread     No
dtype: object
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Arithmetic-Operations">Arithmetic Operations<a class="anchor-link" href="#Arithmetic-Operations">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[157]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fruits</span><span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">10</span><span class="p">,</span> <span class="mi">6</span><span class="p">,</span> <span class="mi">3</span><span class="p">,],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;apples&#39;</span><span class="p">,</span> <span class="s1">&#39;oranges&#39;</span><span class="p">,</span> <span class="s1">&#39;bananas&#39;</span><span class="p">])</span>
<span class="n">fruits</span> <span class="o">+</span> <span class="mi">1</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[157]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>apples     11
oranges     7
bananas     4
dtype: int64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[158]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">np</span><span class="o">.</span><span class="n">sqrt</span><span class="p">(</span><span class="n">fruits</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[158]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>apples     3.162278
oranges    2.449490
bananas    1.732051
dtype: float64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[166]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">fruits</span><span class="p">[[</span><span class="s1">&#39;bananas&#39;</span><span class="p">,</span> <span class="s1">&#39;oranges&#39;</span><span class="p">]]</span> <span class="o">*</span> <span class="mi">10</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[166]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>bananas    30
oranges    60
dtype: int64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Pandas-DataFrames">Pandas DataFrames<a class="anchor-link" href="#Pandas-DataFrames">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Create">Create<a class="anchor-link" href="#Create">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[171]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># We create a dictionary of Pandas Series </span>
<span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">,</span> <span class="mi">45</span><span class="p">])}</span>

<span class="c1"># We print the type of items to see that it is a dictionary</span>
<span class="nb">print</span><span class="p">(</span><span class="nb">type</span><span class="p">(</span><span class="n">items</span><span class="p">))</span>
<span class="n">shopping_carts</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>
<span class="n">shopping_carts</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>&lt;class &#39;dict&#39;&gt;
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[171]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>245.0</td>
      <td>40</td>
    </tr>
    <tr>
      <th>1</th>
      <td>25.0</td>
      <td>110</td>
    </tr>
    <tr>
      <th>2</th>
      <td>55.0</td>
      <td>500</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NaN</td>
      <td>45</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[246]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Create DF from csv</span>
<span class="c1"># df = pd.read_csv(&#39;myfile.csv&#39;)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[172]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># We create a dictionary of Pandas Series </span>
<span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">,</span> <span class="mi">45</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">])}</span>

<span class="c1"># We print the type of items to see that it is a dictionary</span>
<span class="nb">print</span><span class="p">(</span><span class="nb">type</span><span class="p">(</span><span class="n">items</span><span class="p">))</span>
<span class="n">shopping_carts</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>
<span class="n">shopping_carts</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>&lt;class &#39;dict&#39;&gt;
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[172]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[178]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Creating DF Using Subset of Dict</span>

<span class="c1"># We Create a DataFrame that only has selected items for Alice</span>
<span class="n">alice_sel_shopping_cart</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">,</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">],</span> <span class="n">columns</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Alice&#39;</span><span class="p">])</span>
<span class="n">alice_sel_shopping_cart</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[178]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>glasses</th>
      <td>110</td>
    </tr>
    <tr>
      <th>bike</th>
      <td>500</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Attributes">Attributes<a class="anchor-link" href="#Attributes">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[174]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">,</span> <span class="mi">45</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">])}</span>
<span class="n">shopping_carts</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>

<span class="n">shopping_carts</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[174]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(5, 2)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[175]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">shopping_carts</span><span class="o">.</span><span class="n">ndim</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[175]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>2</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[176]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">shopping_carts</span><span class="o">.</span><span class="n">columns</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[176]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>Index([&#39;Bob&#39;, &#39;Alice&#39;], dtype=&#39;object&#39;)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[177]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">shopping_carts</span><span class="o">.</span><span class="n">values</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[177]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>array([[245., 500.],
       [ nan,  40.],
       [ nan, 110.],
       [ 25.,  45.],
       [ 55.,  nan]])</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Accessing-Data">Accessing Data<a class="anchor-link" href="#Accessing-Data">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[265]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">,</span> <span class="mi">45</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Charlie&#39;</span><span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">45</span><span class="p">,</span> <span class="mi">90</span><span class="p">,</span> <span class="mi">70</span><span class="p">,</span> <span class="mi">450</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">])}</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>
<span class="n">df</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[265]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Access-column(s)-by-label">Access column(s) by label<a class="anchor-link" href="#Access-column(s)-by-label">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[266]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[[</span><span class="s1">&#39;Bob&#39;</span><span class="p">,</span> <span class="s1">&#39;Alice&#39;</span><span class="p">]]</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[266]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[256]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">loc</span><span class="p">[:,</span> <span class="p">[</span><span class="s1">&#39;Bob&#39;</span><span class="p">,</span> <span class="s1">&#39;Alice&#39;</span><span class="p">]]</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[256]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Access-column(s)-by-index">Access column(s) by index<a class="anchor-link" href="#Access-column(s)-by-index">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[262]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>
<span class="n">df</span><span class="o">.</span><span class="n">iloc</span><span class="p">[:,</span> <span class="p">[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">2</span><span class="p">]]</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[262]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>450.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Access-row(s)-by-label">Access row(s) by label<a class="anchor-link" href="#Access-row(s)-by-label">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[285]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">loc</span><span class="p">[[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">]]</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[285]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>24500</td>
      <td>40</td>
      <td>4500</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>2500</td>
      <td>110</td>
      <td>9000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Access-row(s)-by-index">Access row(s) by index<a class="anchor-link" href="#Access-row(s)-by-index">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[270]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>
<span class="n">df</span><span class="o">.</span><span class="n">iloc</span><span class="p">[[</span><span class="mi">0</span><span class="p">,</span> <span class="mi">2</span><span class="p">]]</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[270]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90.0</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Get-N-rows-from-a-DF">Get N rows from a DF<a class="anchor-link" href="#Get-N-rows-from-a-DF">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[287]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[:</span><span class="mi">3</span><span class="p">]</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[287]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>24500</td>
      <td>40</td>
      <td>4500</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>2500</td>
      <td>110</td>
      <td>9000</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>5500</td>
      <td>500</td>
      <td>7000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Get-N-random-rows-from-a-DF">Get N random rows from a DF<a class="anchor-link" href="#Get-N-random-rows-from-a-DF">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[295]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">sample</span><span class="p">(</span><span class="n">n</span><span class="o">=</span><span class="mi">2</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[295]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>watch</th>
      <td>5500</td>
      <td>500</td>
      <td>7000</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>2500</td>
      <td>110</td>
      <td>9000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Access-element-by-row-and-column-label">Access element by row and column label<a class="anchor-link" href="#Access-element-by-row-and-column-label">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[188]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;Alice&#39;</span><span class="p">][</span><span class="s1">&#39;bike&#39;</span><span class="p">]</span>  <span class="c1"># Column label always comes first</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[188]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>500.0</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Get-all-rows-where-column-value-satisfies-condition">Get all rows where column value satisfies condition<a class="anchor-link" href="#Get-all-rows-where-column-value-satisfies-condition">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[259]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>
<span class="n">df</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;Bob&#39;</span><span class="p">]</span> <span class="o">&gt;</span> <span class="mi">40</span><span class="p">]</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[259]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Modify-DF">Modify DF<a class="anchor-link" href="#Modify-DF">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[212]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">,</span> <span class="mi">45</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Charlie&#39;</span><span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">45</span><span class="p">,</span> <span class="mi">90</span><span class="p">,</span> <span class="mi">70</span><span class="p">,</span> <span class="mi">450</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">])}</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>
<span class="n">df</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[212]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Add-column">Add column<a class="anchor-link" href="#Add-column">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[201]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;Dan&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">]</span>
<span class="n">df</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[201]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
      <th>Dan</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
      <td>45.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90.0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450.0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Append-columns-from-a-DF-to-another-DF">Append columns from a DF to another DF<a class="anchor-link" href="#Append-columns-from-a-DF-to-another-DF">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[272]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">,</span> <span class="mi">45</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Charlie&#39;</span><span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">45</span><span class="p">,</span> <span class="mi">90</span><span class="p">,</span> <span class="mi">70</span><span class="p">,</span> <span class="mi">450</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">])}</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>
<span class="n">df</span>

<span class="n">items_new</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Dan&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),}</span>
<span class="n">df_new</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items_new</span><span class="p">)</span>
<span class="n">df</span><span class="o">.</span><span class="n">join</span><span class="p">(</span><span class="n">df_new</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[272]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
      <th>Dan</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450.0</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Insert-column-at-index">Insert column at index<a class="anchor-link" href="#Insert-column-at-index">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[216]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">,</span> <span class="mi">45</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Charlie&#39;</span><span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">45</span><span class="p">,</span> <span class="mi">90</span><span class="p">,</span> <span class="mi">70</span><span class="p">,</span> <span class="mi">450</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">])}</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>

<span class="n">df</span><span class="o">.</span><span class="n">insert</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="s1">&#39;Dan&#39;</span><span class="p">,</span> <span class="p">[</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">3</span><span class="p">,</span> <span class="mi">4</span><span class="p">,</span> <span class="mi">5</span><span class="p">])</span>
<span class="n">df</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[216]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Dan</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>1</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>2</td>
      <td>40.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>3</td>
      <td>110.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>4</td>
      <td>45.0</td>
      <td>450.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>5</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Add-column-using-sum-of-previous-columns-values">Add column using sum of previous columns values<a class="anchor-link" href="#Add-column-using-sum-of-previous-columns-values">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[217]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;Total&#39;</span><span class="p">]</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;Bob&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;Alice&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;Charlie&#39;</span><span class="p">]</span> <span class="o">+</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;Dan&#39;</span><span class="p">]</span>
<span class="n">df</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[217]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Dan</th>
      <th>Alice</th>
      <th>Charlie</th>
      <th>Total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>1</td>
      <td>500.0</td>
      <td>70.0</td>
      <td>816.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>2</td>
      <td>40.0</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>3</td>
      <td>110.0</td>
      <td>90.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>4</td>
      <td>45.0</td>
      <td>450.0</td>
      <td>524.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Add-rows">Add rows<a class="anchor-link" href="#Add-rows">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[218]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">new_item</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span><span class="p">:</span> <span class="mi">1</span><span class="p">,</span> <span class="s1">&#39;Alice&#39;</span><span class="p">:</span> <span class="mi">2</span><span class="p">,</span> <span class="s1">&#39;Charlie&#39;</span><span class="p">:</span> <span class="mi">2</span><span class="p">}</span>
<span class="n">new_df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">new_item</span><span class="p">,</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;phones&#39;</span><span class="p">])</span>
<span class="n">display</span><span class="p">(</span><span class="n">new_df</span><span class="p">)</span>

<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">append</span><span class="p">(</span><span class="n">new_df</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>phones</th>
      <td>1</td>
      <td>2</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Dan</th>
      <th>Alice</th>
      <th>Charlie</th>
      <th>Total</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>1.0</td>
      <td>500.0</td>
      <td>70.0</td>
      <td>816.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>2.0</td>
      <td>40.0</td>
      <td>45.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>3.0</td>
      <td>110.0</td>
      <td>90.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>4.0</td>
      <td>45.0</td>
      <td>450.0</td>
      <td>524.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>5.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>phones</th>
      <td>1.0</td>
      <td>NaN</td>
      <td>2.0</td>
      <td>2.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Delete-column">Delete column<a class="anchor-link" href="#Delete-column">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[226]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">,</span> <span class="mi">45</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Charlie&#39;</span><span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">45</span><span class="p">,</span> <span class="mi">90</span><span class="p">,</span> <span class="mi">70</span><span class="p">,</span> <span class="mi">450</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">])}</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>
<span class="n">df</span><span class="o">.</span><span class="n">pop</span><span class="p">(</span><span class="s1">&#39;Bob&#39;</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>40.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>110.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>45.0</td>
      <td>450.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Delete-multiple-columns">Delete multiple columns<a class="anchor-link" href="#Delete-multiple-columns">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[231]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">,</span> <span class="mi">45</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Charlie&#39;</span><span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">45</span><span class="p">,</span> <span class="mi">90</span><span class="p">,</span> <span class="mi">70</span><span class="p">,</span> <span class="mi">450</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">])}</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>

<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;Bob&#39;</span><span class="p">,</span> <span class="s1">&#39;Alice&#39;</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">))</span> <span class="c1"># 1 = columns</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
      <td>45.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>70.0</td>
    </tr>
    <tr>
      <th>book</th>
      <td>45.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>450.0</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Delete-multiple-rows">Delete multiple rows<a class="anchor-link" href="#Delete-multiple-rows">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[232]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">drop</span><span class="p">([</span><span class="s1">&#39;watch&#39;</span><span class="p">,</span> <span class="s1">&#39;book&#39;</span><span class="p">],</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">))</span> <span class="c1"># axis=0 =&gt; row / index</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450.0</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h4 id="Transform-values-of-selected-columns">Transform values of selected columns<a class="anchor-link" href="#Transform-values-of-selected-columns">&#182;</a></h4>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[281]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Charlie&#39;</span><span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">45</span><span class="p">,</span> <span class="mi">90</span><span class="p">,</span> <span class="mi">70</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">])}</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>

<span class="n">columns_to_tranform</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Bob&#39;</span><span class="p">,</span> <span class="s1">&#39;Charlie&#39;</span><span class="p">]</span>
<span class="n">df</span><span class="p">[</span><span class="n">columns_to_tranform</span><span class="p">]</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="n">columns_to_tranform</span><span class="p">]</span><span class="o">.</span><span class="n">apply</span><span class="p">(</span><span class="k">lambda</span> <span class="n">x</span><span class="p">:</span> <span class="n">x</span> <span class="o">*</span> <span class="mi">100</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245</td>
      <td>40</td>
      <td>45</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25</td>
      <td>110</td>
      <td>90</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55</td>
      <td>500</td>
      <td>70</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>24500</td>
      <td>40</td>
      <td>4500</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>2500</td>
      <td>110</td>
      <td>9000</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>5500</td>
      <td>500</td>
      <td>7000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[284]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#### Substitute values in columns of a DF</span>
<span class="n">df</span><span class="o">.</span><span class="n">replace</span><span class="p">([</span><span class="mi">40</span><span class="p">,</span> <span class="mi">7000</span><span class="p">],</span> <span class="p">[</span><span class="s1">&#39;Foo&#39;</span><span class="p">,</span> <span class="s1">&#39;Bar&#39;</span><span class="p">])</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[284]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>24500</td>
      <td>Foo</td>
      <td>4500</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>2500</td>
      <td>110</td>
      <td>9000</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>5500</td>
      <td>500</td>
      <td>Bar</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="&#160;Dealing-with-NaN">&#160;Dealing with NaN<a class="anchor-link" href="#&#160;Dealing-with-NaN">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[240]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">,</span> <span class="mi">45</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Charlie&#39;</span><span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">45</span><span class="p">,</span> <span class="mi">90</span><span class="p">,</span> <span class="mi">70</span><span class="p">,</span> <span class="mi">450</span><span class="p">,</span> <span class="mi">1</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;book&#39;</span><span class="p">,</span> <span class="s1">&#39;glasses&#39;</span><span class="p">,</span> <span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">])}</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
      <td>45</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[235]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Counting NaNs</span>
<span class="n">df</span><span class="o">.</span><span class="n">isnull</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[235]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>4</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[237]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Counting non-NaNs</span>
<span class="n">df</span><span class="o">.</span><span class="n">count</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[237]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>11</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[238]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Drop rows with NaNs</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450.0</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[241]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Drop columns with NaNs</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">dropna</span><span class="p">(</span><span class="n">axis</span><span class="o">=</span><span class="mi">1</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>70</td>
    </tr>
    <tr>
      <th>book</th>
      <td>45</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>90</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>450</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[242]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Replace all NaNs with 0</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="mi">0</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70</td>
    </tr>
    <tr>
      <th>book</th>
      <td>0.0</td>
      <td>40.0</td>
      <td>45</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>0.0</td>
      <td>110.0</td>
      <td>90</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>0.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[244]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Forward fill NaNs (value of previous row)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">fillna</span><span class="p">(</span><span class="n">method</span><span class="o">=</span><span class="s1">&#39;ffill&#39;</span><span class="p">,</span> <span class="n">axis</span><span class="o">=</span><span class="mi">0</span><span class="p">))</span> <span class="c1"># Other methods = &#39;backfill&#39;, &#39;linear&#39;. Axis can be 1</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70</td>
    </tr>
    <tr>
      <th>book</th>
      <td>NaN</td>
      <td>40.0</td>
      <td>45</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>NaN</td>
      <td>110.0</td>
      <td>90</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245.0</td>
      <td>500.0</td>
      <td>70</td>
    </tr>
    <tr>
      <th>book</th>
      <td>245.0</td>
      <td>40.0</td>
      <td>45</td>
    </tr>
    <tr>
      <th>glasses</th>
      <td>245.0</td>
      <td>110.0</td>
      <td>90</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25.0</td>
      <td>45.0</td>
      <td>450</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55.0</td>
      <td>45.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Statistical-Analysis">Statistical Analysis<a class="anchor-link" href="#Statistical-Analysis">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[247]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">items</span> <span class="o">=</span> <span class="p">{</span><span class="s1">&#39;Bob&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">245</span><span class="p">,</span> <span class="mi">25</span><span class="p">,</span> <span class="mi">55</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Alice&#39;</span> <span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">40</span><span class="p">,</span> <span class="mi">110</span><span class="p">,</span> <span class="mi">500</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">]),</span>
         <span class="s1">&#39;Charlie&#39;</span><span class="p">:</span> <span class="n">pd</span><span class="o">.</span><span class="n">Series</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="p">[</span><span class="mi">45</span><span class="p">,</span> <span class="mi">90</span><span class="p">,</span> <span class="mi">70</span><span class="p">],</span> <span class="n">index</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;bike&#39;</span><span class="p">,</span> <span class="s1">&#39;pants&#39;</span><span class="p">,</span> <span class="s1">&#39;watch&#39;</span><span class="p">])}</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">items</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>bike</th>
      <td>245</td>
      <td>40</td>
      <td>45</td>
    </tr>
    <tr>
      <th>pants</th>
      <td>25</td>
      <td>110</td>
      <td>90</td>
    </tr>
    <tr>
      <th>watch</th>
      <td>55</td>
      <td>500</td>
      <td>70</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[248]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Describe statistical information of DF</span>
<span class="n">df</span><span class="o">.</span><span class="n">describe</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[248]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Bob</th>
      <th>Alice</th>
      <th>Charlie</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>3.000000</td>
      <td>3.000000</td>
      <td>3.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>108.333333</td>
      <td>216.666667</td>
      <td>68.333333</td>
    </tr>
    <tr>
      <th>std</th>
      <td>119.303534</td>
      <td>247.857486</td>
      <td>22.546249</td>
    </tr>
    <tr>
      <th>min</th>
      <td>25.000000</td>
      <td>40.000000</td>
      <td>45.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>40.000000</td>
      <td>75.000000</td>
      <td>57.500000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>55.000000</td>
      <td>110.000000</td>
      <td>70.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>150.000000</td>
      <td>305.000000</td>
      <td>80.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>245.000000</td>
      <td>500.000000</td>
      <td>90.000000</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[249]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;Bob&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">describeribe</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[249]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>count      3.000000
mean     108.333333
std      119.303534
min       25.000000
25%       40.000000
50%       55.000000
75%      150.000000
max      245.000000
Name: Bob, dtype: float64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[250]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">mean</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[250]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>Bob        108.333333
Alice      216.666667
Charlie     68.333333
dtype: float64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[251]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">max</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[251]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>Bob        245
Alice      500
Charlie     90
dtype: int64</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Data-Visualisation">Data Visualisation<a class="anchor-link" href="#Data-Visualisation">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">import</span> <span class="nn">seaborn</span> <span class="k">as</span> <span class="nn">sb</span>

<span class="n">df</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;pokemon.csv&#39;</span><span class="p">)</span>
<span class="n">display</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">())</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>



<div class="output_html rendered_html output_subarea ">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>species</th>
      <th>generation_id</th>
      <th>height</th>
      <th>weight</th>
      <th>base_experience</th>
      <th>type_1</th>
      <th>type_2</th>
      <th>hp</th>
      <th>attack</th>
      <th>defense</th>
      <th>speed</th>
      <th>special-attack</th>
      <th>special-defense</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>bulbasaur</td>
      <td>1</td>
      <td>0.7</td>
      <td>6.9</td>
      <td>64</td>
      <td>grass</td>
      <td>poison</td>
      <td>45</td>
      <td>49</td>
      <td>49</td>
      <td>45</td>
      <td>65</td>
      <td>65</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>ivysaur</td>
      <td>1</td>
      <td>1.0</td>
      <td>13.0</td>
      <td>142</td>
      <td>grass</td>
      <td>poison</td>
      <td>60</td>
      <td>62</td>
      <td>63</td>
      <td>60</td>
      <td>80</td>
      <td>80</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>venusaur</td>
      <td>1</td>
      <td>2.0</td>
      <td>100.0</td>
      <td>236</td>
      <td>grass</td>
      <td>poison</td>
      <td>80</td>
      <td>82</td>
      <td>83</td>
      <td>80</td>
      <td>100</td>
      <td>100</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>charmander</td>
      <td>1</td>
      <td>0.6</td>
      <td>8.5</td>
      <td>62</td>
      <td>fire</td>
      <td>NaN</td>
      <td>39</td>
      <td>52</td>
      <td>43</td>
      <td>65</td>
      <td>60</td>
      <td>50</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>charmeleon</td>
      <td>1</td>
      <td>1.1</td>
      <td>19.0</td>
      <td>142</td>
      <td>fire</td>
      <td>NaN</td>
      <td>58</td>
      <td>64</td>
      <td>58</td>
      <td>80</td>
      <td>80</td>
      <td>65</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Univariate-Data">Univariate Data<a class="anchor-link" href="#Univariate-Data">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Categorical-data-frequency/count-as-bar-chart">Categorical data frequency/count as bar chart<a class="anchor-link" href="#Categorical-data-frequency/count-as-bar-chart">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">sb</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;generation_id&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[4]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.axes._subplots.AxesSubplot at 0x1a1e8d9f10&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_126_1.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Single color bars</span>
<span class="n">base_color</span> <span class="o">=</span> <span class="n">sb</span><span class="o">.</span><span class="n">color_palette</span><span class="p">()[</span><span class="mi">0</span><span class="p">]</span>
<span class="n">sb</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;generation_id&#39;</span><span class="p">,</span> <span class="n">color</span> <span class="o">=</span> <span class="n">base_color</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[6]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.axes._subplots.AxesSubplot at 0x1a1e7c1e10&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_127_1.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Sort left to right</span>
<span class="n">gen_order</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;generation_id&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span><span class="o">.</span><span class="n">index</span>
<span class="n">sb</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;generation_id&#39;</span><span class="p">,</span> <span class="n">order</span> <span class="o">=</span> <span class="n">gen_order</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[10]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.axes._subplots.AxesSubplot at 0x1a1e21bf10&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_128_1.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[32]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Rotate x tick labels</span>

<span class="c1">## Without rotation</span>
<span class="n">sb</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;type_1&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[32]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.axes._subplots.AxesSubplot at 0x1a1f25b1d0&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_129_1.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[33]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## With rotation</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="n">rotation</span> <span class="o">=</span> <span class="mi">90</span><span class="p">)</span>

<span class="n">sb</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;type_1&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[33]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.axes._subplots.AxesSubplot at 0x1a1f5571d0&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_130_1.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[36]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Plot Y Bars</span>
<span class="n">sb</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">y</span> <span class="o">=</span> <span class="s1">&#39;type_1&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[36]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;matplotlib.axes._subplots.AxesSubplot at 0x1a20035790&gt;</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_131_1.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Categorical-data-relative-frequency-as-bar-chart">Categorical data relative frequency as bar chart<a class="anchor-link" href="#Categorical-data-relative-frequency-as-bar-chart">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[51]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="n">n_points</span> <span class="o">=</span> <span class="n">df</span><span class="o">.</span><span class="n">shape</span><span class="p">[</span><span class="mi">0</span><span class="p">]</span>
<span class="n">max_count</span> <span class="o">=</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;generation_id&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">value_counts</span><span class="p">()</span><span class="o">.</span><span class="n">max</span><span class="p">()</span>
<span class="n">max_percent</span> <span class="o">=</span> <span class="n">max_count</span> <span class="o">/</span> <span class="n">n_points</span>

<span class="n">tick_props</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="n">max_percent</span><span class="p">,</span>  <span class="mf">0.05</span><span class="p">)</span>
<span class="n">tick_names</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;</span><span class="si">{:0.2f}</span><span class="s1">&#39;</span><span class="o">.</span><span class="n">format</span><span class="p">(</span><span class="n">v</span><span class="p">)</span> <span class="k">for</span> <span class="n">v</span> <span class="ow">in</span> <span class="n">tick_props</span><span class="p">]</span>

<span class="n">sb</span><span class="o">.</span><span class="n">countplot</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;generation_id&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">yticks</span><span class="p">(</span><span class="n">tick_props</span> <span class="o">*</span> <span class="n">n_points</span><span class="p">,</span> <span class="n">tick_names</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">ylabel</span><span class="p">(</span><span class="s1">&#39;proportion&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[51]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>Text(0, 0.5, &#39;proportion&#39;)</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_133_1.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Using-Barplot-to-visualise-processed-data-(not-already-stored-as-a-column-value)">Using Barplot to visualise processed data (not already stored as a column value)<a class="anchor-link" href="#Using-Barplot-to-visualise-processed-data-(not-already-stored-as-a-column-value)">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[55]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">isna</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span>
<span class="n">sb</span><span class="o">.</span><span class="n">barplot</span><span class="p">(</span><span class="n">df</span><span class="o">.</span><span class="n">isna</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">()</span><span class="o">.</span><span class="n">index</span><span class="o">.</span><span class="n">values</span><span class="p">,</span> <span class="n">df</span><span class="o">.</span><span class="n">isna</span><span class="p">()</span><span class="o">.</span><span class="n">sum</span><span class="p">())</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="n">rotation</span> <span class="o">=</span> <span class="mi">90</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[55]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13]),
 &lt;a list of 14 Text xticklabel objects&gt;)</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_135_1.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Numerical-data-histograms">Numerical data histograms<a class="anchor-link" href="#Numerical-data-histograms">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[57]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[57]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>species</th>
      <th>generation_id</th>
      <th>height</th>
      <th>weight</th>
      <th>base_experience</th>
      <th>type_1</th>
      <th>type_2</th>
      <th>hp</th>
      <th>attack</th>
      <th>defense</th>
      <th>speed</th>
      <th>special-attack</th>
      <th>special-defense</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>bulbasaur</td>
      <td>1</td>
      <td>0.7</td>
      <td>6.9</td>
      <td>64</td>
      <td>grass</td>
      <td>poison</td>
      <td>45</td>
      <td>49</td>
      <td>49</td>
      <td>45</td>
      <td>65</td>
      <td>65</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>ivysaur</td>
      <td>1</td>
      <td>1.0</td>
      <td>13.0</td>
      <td>142</td>
      <td>grass</td>
      <td>poison</td>
      <td>60</td>
      <td>62</td>
      <td>63</td>
      <td>60</td>
      <td>80</td>
      <td>80</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>venusaur</td>
      <td>1</td>
      <td>2.0</td>
      <td>100.0</td>
      <td>236</td>
      <td>grass</td>
      <td>poison</td>
      <td>80</td>
      <td>82</td>
      <td>83</td>
      <td>80</td>
      <td>100</td>
      <td>100</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>charmander</td>
      <td>1</td>
      <td>0.6</td>
      <td>8.5</td>
      <td>62</td>
      <td>fire</td>
      <td>NaN</td>
      <td>39</td>
      <td>52</td>
      <td>43</td>
      <td>65</td>
      <td>60</td>
      <td>50</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>charmeleon</td>
      <td>1</td>
      <td>1.1</td>
      <td>19.0</td>
      <td>142</td>
      <td>fire</td>
      <td>NaN</td>
      <td>58</td>
      <td>64</td>
      <td>58</td>
      <td>80</td>
      <td>80</td>
      <td>65</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[63]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;speed&#39;</span><span class="p">,</span> <span class="n">bins</span> <span class="o">=</span> <span class="mi">20</span><span class="p">);</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_138_0.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[64]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">bins</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="n">df</span><span class="p">[</span><span class="s1">&#39;speed&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">()</span><span class="o">+</span><span class="mi">5</span><span class="p">,</span> <span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;speed&#39;</span><span class="p">,</span> <span class="n">bins</span> <span class="o">=</span> <span class="n">bins</span><span class="p">);</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_139_0.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[68]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">sb</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;speed&#39;</span><span class="p">]);</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_140_0.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[67]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">sb</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;speed&#39;</span><span class="p">],</span> <span class="n">kde</span><span class="o">=</span><span class="kc">False</span><span class="p">);</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_141_0.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Subplots-(Stack-Plots-Horizontally)">Subplots (Stack Plots Horizontally)<a class="anchor-link" href="#Subplots-(Stack-Plots-Horizontally)">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[74]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span> <span class="o">=</span> <span class="p">[</span><span class="mi">15</span><span class="p">,</span> <span class="mi">5</span><span class="p">])</span>

<span class="n">plt</span><span class="o">.</span><span class="n">subplot</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span>                    <span class="c1"># 1 row, 2 cols, subplot 1</span>
<span class="n">sb</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;speed&#39;</span><span class="p">],</span> <span class="n">kde</span><span class="o">=</span><span class="kc">False</span><span class="p">);</span>

<span class="n">plt</span><span class="o">.</span><span class="n">subplot</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">2</span><span class="p">)</span>                    <span class="c1"># 1 row, 2 cols, subplot 2</span>
<span class="n">sb</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;speed&#39;</span><span class="p">]);</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_143_0.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Plot-Subset-of-Data-(Axis-Range-Limits)">Plot Subset of Data (Axis Range Limits)<a class="anchor-link" href="#Plot-Subset-of-Data-(Axis-Range-Limits)">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[79]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;height&#39;</span><span class="p">);</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_145_0.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[85]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;height&#39;</span><span class="p">);</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xlim</span><span class="p">((</span><span class="mi">0</span><span class="p">,</span> <span class="mi">2</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[85]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(0, 2)</pre>
</div>

</div>

<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_146_1.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Axis-Transformations-(Log-Scale)">Axis Transformations (Log Scale)<a class="anchor-link" href="#Axis-Transformations-(Log-Scale)">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[87]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Original plot (with linear scale)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;weight&#39;</span><span class="p">);</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_148_0.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[97]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Plots with log scales for x-axis</span>
<span class="n">plt</span><span class="o">.</span><span class="n">figure</span><span class="p">(</span><span class="n">figsize</span> <span class="o">=</span> <span class="p">[</span><span class="mi">15</span><span class="p">,</span> <span class="mi">5</span><span class="p">])</span>

<span class="n">plt</span><span class="o">.</span><span class="n">subplot</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">1</span><span class="p">)</span>    
<span class="n">sb</span><span class="o">.</span><span class="n">distplot</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;weight&#39;</span><span class="p">],</span> <span class="n">kde</span><span class="o">=</span><span class="kc">False</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xscale</span><span class="p">(</span><span class="s1">&#39;log&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">subplot</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span> <span class="mi">2</span><span class="p">,</span> <span class="mi">2</span><span class="p">)</span>    
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;weight&#39;</span><span class="p">);</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xscale</span><span class="p">(</span><span class="s1">&#39;log&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_149_0.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[98]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">## Changing x range, whilst in log scale to better visualise data distribution</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xscale</span><span class="p">(</span><span class="s1">&#39;log&#39;</span><span class="p">)</span>

<span class="nb">min</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">log10</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;weight&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">min</span><span class="p">())</span>
<span class="nb">max</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">log10</span><span class="p">(</span><span class="n">df</span><span class="p">[</span><span class="s1">&#39;weight&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">max</span><span class="p">())</span>
<span class="n">bins</span> <span class="o">=</span> <span class="mi">10</span> <span class="o">**</span> <span class="n">np</span><span class="o">.</span><span class="n">arange</span><span class="p">(</span><span class="nb">min</span><span class="p">,</span> <span class="nb">max</span> <span class="o">+</span> <span class="mf">0.1</span><span class="p">,</span> <span class="mf">0.1</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">(</span><span class="n">data</span> <span class="o">=</span> <span class="n">df</span><span class="p">,</span> <span class="n">x</span> <span class="o">=</span> <span class="s1">&#39;weight&#39;</span><span class="p">,</span> <span class="n">bins</span> <span class="o">=</span> <span class="n">bins</span><span class="p">);</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_150_0.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Bivariate-Data">Bivariate Data<a class="anchor-link" href="#Bivariate-Data">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Pairwise-Relationship-Between-Numerical-Columns">Pairwise Relationship Between Numerical Columns<a class="anchor-link" href="#Pairwise-Relationship-Between-Numerical-Columns">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[102]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">sb</span><span class="o">.</span><span class="n">pairplot</span><span class="p">(</span><span class="n">df</span><span class="p">,</span> <span class="n">hue</span><span class="o">=</span><span class="s1">&#39;generation_id&#39;</span><span class="p">);</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_153_0.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h3 id="Categorical-daya-grouped-by-another-label">Categorical daya grouped-by another label<a class="anchor-link" href="#Categorical-daya-grouped-by-another-label">&#182;</a></h3>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">df</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[3]:</div>



<div class="output_html rendered_html output_subarea output_execute_result">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>species</th>
      <th>generation_id</th>
      <th>height</th>
      <th>weight</th>
      <th>base_experience</th>
      <th>type_1</th>
      <th>type_2</th>
      <th>hp</th>
      <th>attack</th>
      <th>defense</th>
      <th>speed</th>
      <th>special-attack</th>
      <th>special-defense</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>bulbasaur</td>
      <td>1</td>
      <td>0.7</td>
      <td>6.9</td>
      <td>64</td>
      <td>grass</td>
      <td>poison</td>
      <td>45</td>
      <td>49</td>
      <td>49</td>
      <td>45</td>
      <td>65</td>
      <td>65</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>ivysaur</td>
      <td>1</td>
      <td>1.0</td>
      <td>13.0</td>
      <td>142</td>
      <td>grass</td>
      <td>poison</td>
      <td>60</td>
      <td>62</td>
      <td>63</td>
      <td>60</td>
      <td>80</td>
      <td>80</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>venusaur</td>
      <td>1</td>
      <td>2.0</td>
      <td>100.0</td>
      <td>236</td>
      <td>grass</td>
      <td>poison</td>
      <td>80</td>
      <td>82</td>
      <td>83</td>
      <td>80</td>
      <td>100</td>
      <td>100</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>charmander</td>
      <td>1</td>
      <td>0.6</td>
      <td>8.5</td>
      <td>62</td>
      <td>fire</td>
      <td>NaN</td>
      <td>39</td>
      <td>52</td>
      <td>43</td>
      <td>65</td>
      <td>60</td>
      <td>50</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>charmeleon</td>
      <td>1</td>
      <td>1.1</td>
      <td>19.0</td>
      <td>142</td>
      <td>fire</td>
      <td>NaN</td>
      <td>58</td>
      <td>64</td>
      <td>58</td>
      <td>80</td>
      <td>80</td>
      <td>65</td>
    </tr>
  </tbody>
</table>
</div>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[26]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="n">chart</span> <span class="o">=</span> <span class="n">sb</span><span class="o">.</span><span class="n">catplot</span><span class="p">(</span><span class="n">x</span><span class="o">=</span><span class="s1">&#39;type_1&#39;</span><span class="p">,</span> <span class="n">kind</span><span class="o">=</span><span class="s1">&#39;count&#39;</span><span class="p">,</span> <span class="n">hue</span><span class="o">=</span><span class="s1">&#39;generation_id&#39;</span><span class="p">,</span> <span class="n">data</span><span class="o">=</span><span class="n">df</span><span class="p">,</span> <span class="n">height</span><span class="o">=</span><span class="mi">10</span><span class="p">,</span> <span class="n">aspect</span><span class="o">=</span><span class="mi">10</span><span class="o">/</span><span class="mf">7.5</span><span class="p">);</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="n">rotation</span> <span class="o">=</span> <span class="mi">90</span><span class="p">);</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="/assets/blog/cheat-sheets/python/output_156_0.png"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Anaconda">Anaconda<a class="anchor-link" href="#Anaconda">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="List-envs">List envs<a class="anchor-link" href="#List-envs">&#182;</a></h2>
<pre><code>conda info --envs</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Activate-env">Activate env<a class="anchor-link" href="#Activate-env">&#182;</a></h2>
<pre><code>conda activate &lt;env_name&gt;</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Update-all-packages">Update all packages<a class="anchor-link" href="#Update-all-packages">&#182;</a></h2>
<pre><code>conda upgrade -all</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Install-package">Install package<a class="anchor-link" href="#Install-package">&#182;</a></h2>
<pre><code>conda install package_name

## specifying package version
conda install numpy=1.10</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Remove-package">Remove package<a class="anchor-link" href="#Remove-package">&#182;</a></h2>
<pre><code>conda remove package_name</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Search-package">Search package<a class="anchor-link" href="#Search-package">&#182;</a></h2>
<pre><code>conda search *search_term*</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="List-packages">List packages<a class="anchor-link" href="#List-packages">&#182;</a></h2>
<pre><code>conda list</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Jupyter">Jupyter<a class="anchor-link" href="#Jupyter">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Convert-notebook-to-html">Convert notebook to html<a class="anchor-link" href="#Convert-notebook-to-html">&#182;</a></h2>
<pre><code>jupyter nbconvert --to html notebook.ipynb

# Other formats
# https://nbconvert.readthedocs.io/en/latest/usage.html</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Add-TOC">Add TOC<a class="anchor-link" href="#Add-TOC">&#182;</a></h2><p>Ref: <a href="https://towardsdatascience.com/jupyter-tools-to-increase-productivity-7b3c6b90be09">https://towardsdatascience.com/jupyter-tools-to-increase-productivity-7b3c6b90be09</a></p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span> 
</pre></div>

    </div>
</div>
</div>

</div>
    </div>
  </div>
