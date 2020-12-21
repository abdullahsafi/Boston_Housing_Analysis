---
title: Exectutive Summary | Boston Data Set

# Use letters for affiliations
author:
  - name: 480440172, 490175477, 480561916, 480550367, 470500790
address:
    address: DATA2002 Group M13-07
    
# Optional: line of arbitrary text with additional information.
# Could be used, for example, to mention the bibliographic info in a post-print.
# If not specified, defaults to "This version was compiled on \today"
date_subtitle: The University of Sydney 2019 Semester Two

# For footer text  TODO(fold into template, allow free form two-authors)
lead_author_surname: Author and Author

# Place eg a DOI URL or CRAN Package URL here
doi_footer: "https://cran.r-project.org/package=YourPackage"

# Abstract
abstract: |
  A city's housing is a crucial and important factor for the well-being of residents and plays quite a significant role in the sustainability of an economy. Rising house prices generally equate to higher rates of [economic growth](https://www.economicshelp.org/blog/21636/housing/how-the-housing-market-affects-the-economy/) due to encourage consumer spending. But this can also see first-time buyers and families struggling with increasingly unaffordable prices in the market.
  This leads us to the purpose of this investigation, which is to determine and discover what factors and variables may be significantly impacting the median house prices. The findings of this report suggest that factors such as crime rates, nitric oxide concentration and several others do have some statistically significant effect on the median house price in boston. 


# Optional: Acknowledgements
acknowledgements: |
  This template package builds upon, and extends, the work of the excellent
  [rticles](https://cran.r-project.org/package=rticles) package, and both packages rely on the
  [PNAS LaTeX](http://www.pnas.org/site/authors/latex.xhtml) macros. Both these sources are
  gratefully acknowledged as this work would not have been possible without them.  Our extensions
  are under the same respective licensing term
  ([GPL-3](https://www.gnu.org/licenses/gpl-3.0.en.html) and
  [LPPL (>= 1.3)](https://www.latex-project.org/lppl/)).

# Optional: One or more keywords
#keywords:
#  - one
#  - two
#  - optional
#  - keywords
#  - here

# Paper size for the document, values of letter and a4
papersize: letter

# Font size of the document, values of 9pt (default), 10pt, 11pt and 12pt
fontsize: 11pt

# Optional: Force one-column layout, default is two-column
#one_column: true

# Optional: Enables lineno mode, but only if one_column mode is also true
#lineno: true

# Optional: Enable one-sided layout, default is two-sided
#one_sided: true

# Optional: Enable section numbering, default is unnumbered
#numbersections: true

# Optional: Specify the depth of section number, default is 5
#secnumdepth: 5

# Optional: Skip inserting final break between acknowledgements, default is false
skip_final_break: true

# Optional: Bibliography 
bibliography: pinp

# Optional: Enable a 'Draft' watermark on the document
#watermark: true

# Customize footer, eg by referencing the vignette
footer_contents: "YourPackage Vignette"

# Produce a pinp document
output: pinp::pinp

# Required: Vignette metadata for inclusion in a package.
#\cite{PeerJ:Rcpp}
vignette: >
  %\VignetteIndexEntry{YourPackage-vignetteentry}
  %\VignetteKeywords{YourPackage, r, anotherkeyword}
  %\VignettePackage{YourPackage}
  %\VignetteEngine{knitr::rmarkdown}
---

# 1. Introduction 
According to the database, we found that the price difference between Boston houses is significant. The database has 506 cases and 14 variables. The purpose of our report is to explore and evaluate the factors affecting Boston's housing prices using multiple regression analysis. The main question that we aim to investigate whether the full-value property-tax rate per \$10,000 and weighted distances to five Boston employment centres is a factor influencing the median value of owner-occupied homes is $1000's. Housing prices are affected by factors such as but not limited to: location, demographics, unemployment rates, number of rooms, etc. Multiple regression uses multiple predictor variables to predict an outcome which justifies why this model can be used for the Boston Housing dataset analysis.

# 2. The Data set

To complete this investigation a dataset containing information collected by the U.S Census Service in 1978 is used. This sample consists of 506 entries and holds information concerning housing in the area of Boston Mass. The dataset was obtained from StatLib archive but was originally published by Harrison, D. and Rubinfeld, D.L.. The CSV file used in this report was obtained from the StatLib archive at “http://lib.stat.cmu.edu/datasets/boston” and has a total of 506 entries. 

Additionally, the dataset has 14 variables which represent; crime rate per capita, the proportion of residential land zones for lots over 25,000 square feet, the proportion of non-retail business acres, if it was bound by a river, nitric oxides concentration, the average number of rooms per dwelling, proportion of owner occupied units since 1940, the distances to five Boston employment centres, the accessibility of radial highways,  the pupil teacher ratio by town, the proportion of African Americans by town, the percentage lower status of the population and lastly, the median value of owner-occupied homes in $1000’s.  


# 3. Analysis

After initial analysis of the dataset, CHAS is dropped from the data frame, because it is a binary dummy variable that states whether a track bounds a river, and since it is binary, it can not be used in multiple regression. The variable MEDV is the Median value of owner-occupied homes in $1000's and is the variable of interest since it will assist in establishing what affects the prices of homes. 
We perform a multiple regression analysis on the variable MEDV using a backwards stepwise procedure on a full model (Figure 5). To rid of insignificant variables we use the AIC backwards search model. After the step wise procedure, the variables AGE and INDUS were dropped as they were proven to be statistically insignificant to MEDV in our model. 

## 3.1 *Assumptions*

We then decided to check the model and our assumptions, and after viewing our residuals versus fitted plot (Figure 2), we decided to do a log transformation on the model since there was a distinct pattern. Our regression assumptions were met after our log transformation:




As seen in the residuals versus fitted plot there is no obvious patterns and therefore it does not seem that the model has been misidentified. Regarding homoskedasticity, the residuals don’t appear to be fanning out or changing their variability over the range of the fitted values so the constant error variance assumption is met. in the QQ plot, the points are reasonably close to the diagonal line, although it is possible to argue that the points may be slightly over-dispersed. Considering that the sample data initially contained 506 entries it is understandable to have some deviation which is not severe enough to cause too much concern. The normality assumption is at least approximately satisfied.
Looking at the R^2 value (multiple R-squared) from the summary output, ~79% of the variability is explained by the regression on the variables listed above. 

\begin{figure}

{\centering \includegraphics[width=0.95\linewidth]{assumptionSReport} 

}

\caption{Assumption Checking}\label{fig:figex}
\end{figure}


# 4. Results

There is evidence that indicates a weak correlation between Tax and Median value of the property, weighted distances to five Boston employment centres on MedV. Additionally, when a linear regression is performed for them, a relatively weak linear relationship was found for the comparisons between these 3 variables. This was checked by obtaining the R^2 values of them which were 0.0606 and 0.1157 respectively. 
 
From the multiple regression analysis, there are 2 variables that were found not to be significantly correlated. Namely AGE and INDUS. The remaining 11 variables showed significant correlation with the Median value of the properties. 
 
The model we chose is as follows:


$\widehat{MEDV} = 36.341 - 0.108\times\text{CRIM} + 0.045\times\text{ZN} + 2.718\times\text{CHAS} - 17.376\times\text{NOX} + 3.801\times\text{RM} - 1.492\times\text{DIS} - 0.0118\times\text{TAX} - 0.012\times\text{PTRATIO} + 0.009\times\text{B} -  0.522\times\text{LSTAT}$

## Discussion and Conclusion

This report generally has many interesting findings regarding the house market. However, despite this there are many limitations to this study which potentially have the ability to alter and influence results. The boston dataset used may have some issues. For instance, some of the data was sourced from outside of Delve and may be somewhat suspect since there is not a definite reliable source for some of the comparisons in the dataset. Being published in 1978, it is clear the data is also quite relatively old and this would not necessarily impact the results but may introduce some bias to the general questions about the median house market in today's society. In a future analysis, it would defenifenity be more appropriate to investigate a data set that is recent and reliable to ensure contemporary and relevant results. In addition to this, there is some evident departure on the qq-plot and there is a small pattern of over-fitting, however, the dataset is quite large and this is somewhat expected when dealing with larger datasets. Despite this, perhaps in future investigations it will be more fitting to have a deeper analysis into the variables and a wider range of model selection.

In conclusion, from our multiple regression, we found that housing prices in Boston is found to be not significantly correlated with (AGE) and proportion of non-retail business acres per town (INDUS). This model was reasonably accurate in predicting median house prices (R^2 = 0.74). The linear models show that tax rate and distance to employment centres are a relatively weak direct relationship, so we cannot make sure it is a factor influencing housing price.These model show multiple regression is an excellent way to analyse data, but in the future, we should consider deeper analyse.


## References 

Here we differ from PNAS and suggest natbib. References will appear in
author-year form. Use `\citet{}`, `\citep{}`, etc as usual.

We default to the `jss.bst` style. To switch to a different bibliography
style, please use `biblio-style: style` in the YAML header.


## Inline R Code 

The PNAS sample included a fixed PNG image here, but this document prefers
to show the results and embedding of _R_ code. 




## Single column equations 

Authors may use 1- or 2-column equations in their article, according to
their preference.

To allow an equation to span both columns, options are to use the
`\begin{figure*}...\end{figure*}` environment mentioned above for
figures. The `\begin{widetext}...\end{widetext}` environment as shown
in equation \ref{eqn:example} below is deprecated, but \LaTeX commands
`\onecolumn` and `\twocolumn` work fine.

Please note that this option may run into problems with floats and
footnotes, as mentioned in the [cuted package
documentation](http://texdoc.net/pkg/cuted). In the case of problems
with footnotes, it may be possible to correct the situation using
commands `\footnotemark` and `\footnotetext`.

$\widehat{MEDV} = 36.341 - 0.108\times\text{CRIM} + 0.045\times\text{ZN} + 2.718\times\text{CHAS} - 17.376\times\text{NOX} + 3.801\times\text{RM} - 1.492\times\text{DIS} - 0.0118\times\text{TAX} - 0.012\times\text{PTRATIO} + 0.009\times\text{B} -  0.522\times\text{LSTAT}$

\begin{equation}
  \begin{aligned}
(x+y)^3&=(x+y)(x+y)^2\\
       &=(x+y)(x^2+2xy+y^2) \\
       &=x^3+3x^2y+3xy^3+x^3. 
       \label{eqn:example} 
  \end{aligned}
\end{equation}


\begin{figure}

{\centering \includegraphics{mypaper_files/figure-latex/unnamed-chunk-1-1} 

}

\caption{Narrow ggplot2 figure}\label{fig:unnamed-chunk-1}
\end{figure}
<!-- pandoc writes all tables using longtable, which fails in 2-column mode

  Species                    CBS     CV     G3
  ----------------------- ------ ------ ------
  1\. Acetaldehyde           0.0    0.0    0.0
  2\. Vinyl alcohol          9.1    9.6   13.5
  3\. Hydroxyethylidene     50.8   51.2   54.0

  : Comparison of the fitted potential energy surfaces and ab initio
  benchmark electronic energy calculations

-->

