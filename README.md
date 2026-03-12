# KalpiCast - Greek Pollster Ratings Data  
**Last update: January 2026**  

Full methodology description available at: https://kalpicast.gr/en/methodology/pollster-ratings

### Column	Description (pollster_ratings.csv)
- starRating:	A star rating ranging from 1 – 5 based exclusively on balancedScore (more stars is better)
- balanacedScore:	Score combining logScore and biasScore with equal weights (lower is better)
- logScore:	The standardized and shrunk mean_neg_logL_pm. The shrinkage is performed using the formula:\
  Shrunk value = $`m_0*s_0^2/(s_0^2+s^2) + m*s^2/(s_0^2+s^2)`$,  
  where m0=Mean (across pollsters) of IQR-winsorized mean_neg_logL_pm, s0=tau (Sampling heterogeneity of the estimator, as estimated by DerSimonian–Laird formula), m=Pollster specific mean_neg_logL_pm, s=Pollster specific sampling std of estimator= std_neg_logL_pm/sqrt(elections_eval)
- biasScore:	The standardized and shrunk rms_mean_bias_pm. The shrinkage is performed using the Bayesian Stacking Normal-Normal formula:\
  Shrunk value = $`m_0*s_0^2/(s_0^2+s^2) + m*s^2/(s_0^2+s^2)`$,\
  where m0=Mean (across pollsters) of IQR-winsorized  rms_mean_bias_pm, s0=tau (Sampling heterogeneity of the RMS estimator, as estimated by DerSimonian–Laird formula), m=Pollster specific rms_mean_bias_pm, s=Pollster specific sampling std of estimator= std_rms_mean_bias_pm/sqrt(elections_eval)
- elections_eval:	The number of elections used for the evaluation of the pollster. Higher elections allow for larger confidence in the performance and lower numbers increase the shrinkage making scores more average,
- w_prior_logScore:	The Bayesian stacking weight of the prior for logScore
- w_prior_biasScore:	The Bayesian stacking weight of the prior for biasScore
- mean_neg_logL:	The weighted mean negative log-likelihood of pollster’s polls, according to actual election outcome and poll effective sample size (adjusted by days till election). The weighting is a time weight giving larger weights to more recent elections, specifically a negative exponential formula with half life of 4 years is used.
- mean_neg_logL_pm:	The relative (plus-minus) version of mean_neg_logL. Essentially, the mean_neg_logL values within each election are standardized to make sure the election specific difficulty does not affect overall pollster performance.
- std_neg_logL_pm:	The pollster specific weighted sample standard deviation of relative (pm) negative log-likelihood of pollster’s polls according to actual election outcome and poll effective sample size (adjusted by days till election). The weighting is a time weight giving larger weights to more recent elections, specifically a negative exponential formula with half life of 4 years is used. If pollster is evaluated in one election only (making std undefined), the industry-wide 95 percentile of stds is imputed instead.
- mean_rmse:	The weighted mean of within election RMSE of pollster’s polls. In practice this is the mean absolute error because one poll per pollster is used for each election. The weighting is a time weight giving larger weights to more recent elections, specifically a negative exponential formula with half life of 4 years is used.
- mean_rmse_pm:	The relative (plus-minus) version of mean_rmse. Essentially, the mean_rmse values within each election are log-transformed and standardized to make sure the election specific difficulty does not affect overall pollster performance.
- rms_mean_bias:	The RMS (across parties) of weighted mean bias of pollster’s polls. The weighting is a time weight giving larger weights to more recent elections, specifically a negative exponential formula with half life of 4 years is used.
- rms_mean_bias_pm:	The relative (plus-minus) version of rms_mean_bias. Essentially, the mean_bias values within each election are standardized to make sure the election specific difficulty does not affect overall pollster performance.
- std_rms_,mean_bias_pm:	The pollster specific underlying weighted sample standard deviation of relative (pm) RMS (across parties) mean bias of pollster’s polls. Since the underlying distribution, where RMS draws from, cannot be accessed directly, the delta method is used to compute the std. The weighting is a time weight giving larger weights to more recent elections, specifically a negative exponential formula with half life of 4 years is used. If pollster is evaluated in one election only (making ssample std undefined), the pooled (among all other pollsters) std is used.
- elections_eval_party:	The number of elections used for the evaluation of the pollster, where the party was been tracked.
- mean_bias_party:	The mean bias pollster exhibits towards the party. Positive values favor the party. This may be misleading because it has not been adjust to remove election specific effects.
- mean_bias_party_pm:	The relative (plus-minus) version of mean_bias_party. Essentially, the mean_bias_party values within each election are standardized to make sure the election specific difficulty does not affect overall pollster performance.
- mse_party:	The mean squared error pollster exhibits for the party. This may be misleading because it has not been adjust to remove election specific effects.
- mse_party_pm:	The relative (plus-minus) version of mse_party. Essentially, the mses_party values within each election are standardized to make sure the election specific difficulty does not affect overall pollster performance.