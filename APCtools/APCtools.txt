# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Age Period Cohort (APC) analysis Use create_APCsummary (APCtools) With (In) R Software
install.packages("APCtools")
install.packages("gam")
library("gam")
library("APCtools")
library("dplyr")
library("ggplot2")
library("ggpubr")
library("mgcv")
theme_set(theme_minimal())
APCtools = read.csv("https://raw.githubusercontent.com/timbulwidodostp/APCtools/main/APCtools/APCtools.csv",sep = ";")
# Estimation Age Period Cohort (APC) analysis Use create_APCsummary (APCtools) With (In) R Software
model_pure <- gam(mainTrip_distance ~ te(age, period, bs = "ps", k = c(8,8)), data = APCtools)
model_cov  <- gam(mainTrip_distance ~ te(age, period, bs = "ps", k = c(8,8)) + residence_region + household_size + s(household_income), data = APCtools)
model_list <- list("pure model" = model_pure, "covariate model" = model_cov)
create_APCsummary(model_list = model_list, dat = APCtools)
summary_list <- create_modelSummary(model_list)
summary_list
# Age Period Cohort (APC) analysis Use create_APCsummary (APCtools) With (In) R Software
# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Finished