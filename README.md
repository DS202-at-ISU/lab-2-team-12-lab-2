
<!-- README.md is generated from README.Rmd. Please edit the README.Rmd file -->

# Lab report \#1

Follow the instructions posted at
<https://ds202-at-isu.github.io/labs.html> for the lab assignment. The
work is meant to be finished during the lab time, but you have time
until Monday evening to polish things.

Include your answers in this document (Rmd file). Make sure that it
knits properly (into the md file). Upload both the Rmd and the md file
to your repository.

All submissions to the github repo will be automatically uploaded for
grading once the due date is passed. Submit a link to your repository on
Canvas (only one submission per team) to signal to the instructors that
you are done with your submission.

## Step 1

Inspect first few lines of dataset:

The different variables are Parcel ID, Address, Style, Occupancy, Sale
Date, Sale Price, Multi Sale (if the sale was a package deal), Year
Built, Acres, TotalLivingArea (sf), Bedrooms, FinishedBsmtArea (sf),
LotArea (sf), AC (if the property has AC), FirePlace (if the property
has a fireplace), and Neighborhood.

The type of variable and their data range can be pictured with
summary(ames):

## Step 2

The variable of interest is Sale Price.

## Step 3

``` r
summary(ames$`Sale Price`)
```

    ##     Min.  1st Qu.   Median     Mean  3rd Qu.     Max. 
    ##        0        0   170900  1017479   280000 20500000

``` r
ggplot(ames, aes(x = `Sale Price`)) +
  geom_histogram(binwidth = 50000, fill = "skyblue", color = "black") +
  labs(title = "Histogram of Sale Price", x = "Sale Price", y = "Count")
```

![](README_files/figure-gfm/step3-1.png)<!-- -->

When we look at the summary() function we have:

Min. 0

1st Qu. 0

Median 170900

Mean 1017479

3rd Qu. 280000

Max. 20500000

This tells us that while most properties fall within a modest range,
there are some extreme values up to 20.5 million, and notably, a minimum
of 0, which is unusual for a sales price.

The histogram typically shows a right-skewed distribution. It means that
most properties are sold at lower prices.

A oddity is that the minimum sale price is 0, and the first quartile is
also 0. This suggests that a significant number of records have a sale
price of 0.

It might indicate data entry errors.

These could represent properties transferred without a sale.

## Step 4

Kylie:

Lucas:

``` r
ggplot(ames, aes(x = `FinishedBsmtArea (sf)`)) +
  geom_histogram(binwidth = 100, fill = "lightgreen", color = "black") +
  labs(title = "Histogram of Finished Bsmt Area (sf)",
       x = "Finished Bsmt Area (sf)",
       y = "Count")
```

    ## Warning: Removed 2682 rows containing non-finite outside the scale range
    ## (`stat_bin()`).

![](README_files/figure-gfm/step4-1.png)<!-- -->

``` r
ggplot(ames, aes(x = `FinishedBsmtArea (sf)`, y = `Sale Price`)) +
  geom_point(alpha = 0.6, color = "steelblue") +
  coord_cartesian(ylim = c(0, 2000000))+
  labs(title = "Scatterplot of Sale Price vs. Finished Basement Area (sf)",
       x = "Finished Basement Area (sf)",
       y = "Sale Price")
```

    ## Warning: Removed 2682 rows containing missing values or values outside the scale range
    ## (`geom_point()`).

![](README_files/figure-gfm/step4.1-1.png)<!-- -->

Most properties cluster under 2,000 square feet of finished basement
area. Most of the points lie at or near zero sale price, which is
unusual and may represent non-market transactions, data entry errors, or
special cases. At the higher end, there are outliers with very large
basement areas or exceptionally high sale prices that also warrant
further investigation.

Aiden:
