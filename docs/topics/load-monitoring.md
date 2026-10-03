# Load monitoring and adaptation checks

**Last checked:** 2026-10-02

**Scope:** [Questions 20 and 21](../index.md#question-map) — what training-load numbers mean, and which measurements actually tell a trained amateur (about 7–12 total training hours/week; goals VO₂max, threshold power, and general fitness) whether the program is working. This is a living topic note, not a prescription service and not a transcript commentary. No transcript was supplied, so nothing below is attributed to one.

**Read with:** [platform home](../index.md) · [shared terms](../CONTEXT.md) · [source registry](../evidence/bibliography.md). Intensity distribution, durability physiology, fueling, and sleep sit in their own topics. This note uses them only where they change how a number should be read.

Reading order: [Previous — strength and warm-ups](strength-warmups-mobility.md) · [Next — designing a recoverable program](program-design.md).

**Question navigation**

- [Q20. Training-load metrics](#q20-training-load-metrics) — TSS, normalized power, intensity factor, CTL/ATL/TSB, TRIMP, session-RPE, kilojoules, hours, heart-rate load
- [Q21. Monitoring adaptation](#q21-monitoring-adaptation) — FTP, critical power, W′, 5- and 20-minute power, the power-duration curve, heart rate, decoupling, resting heart rate, HRV, wellness, and a decision workflow
- [Metric comparison table](#metric-comparison-table)
- [Conflict-resolution workflow](#conflict-resolution-workflow)
- [Open questions](#open-questions)
- [References](#references)

Evidence was checked through 2026-10-02, including a targeted 2025–2026 search. Classifications apply to the stated claim, not to “monitoring” as a whole: **Strong evidence**, **Moderate evidence**, **Plausible but uncertain**, or **Mostly coaching practice**.

---

## How to read the numbers

Two families of quantity get conflated in coaching software.

**External load** is what the bicycle did: duration, kilojoules, average power, normalized power, time in power zones. **Internal load** is what it cost the athlete: heart rate, a heart-rate training impulse, session rating of perceived exertion (session-RPE), and the next-day wellness report. Impellizzeri, Marcora, and Coutts (2019) restated that split fifteen years after they introduced it: the training process has a measurable external component and a measurable internal component, and they are not the same construct. Mujika’s endurance-load review (2017) and the Bourdon consensus statement (2017) make the same practical point. Halson (2014) is blunter: many candidate markers exist, few have strong evidence, and no single marker is definitive.

A third family is the **outcome**: did sustainable power, a standardized time trial, or the ability to complete the planned session actually change? Chronic training load (CTL) is not in this family. It is a smoothed sum of past session scores. Calling it “fitness,” as TrainingPeaks does in the product interface, is a label, not a measurement (TrainingPeaks performance-management chart, page updated 16 May 2026).

---

## Durable conclusions

<a id="mon-c01"></a>
### MON-C01 — TSS, normalized power, IF, CTL, ATL, and TSB are bookkeeping models, not measured fitness

**Classification:** Strong evidence

**Claim.** Training stress score (TSS), normalized power (NP), intensity factor (IF), chronic training load (CTL), acute training load (ATL), and training stress balance (TSB) are deterministic transforms of a power file and a user-entered threshold. One hour at the entered functional threshold power (FTP) scores 100 TSS by construction. A CTL of 60 is not a fitness test result.

**Support.** Friel, on the TrainingPeaks site (article first published 2009, updated 13 April 2026), gives the vendor formula and the defining case:

TSS = (seconds × NP × IF) / (FTP × 3600) × 100

with IF = NP / FTP. He states that FTP is, by definition, 100 TSS for one hour. Coggan’s TrainingPeaks explainer (published 2016, updated 11 May 2026) defines IF as NP divided by the rider’s threshold power, and describes NP as an adjustment for variable power so that a ride can be compared with the constant power that would have had a similar physiological “cost.” The same page is explicit that the algorithm is a model of two ideas: physiological responses are not instantaneous, and several responses (glycogen use, lactate, stress hormones) are curvilinear with intensity. It does not present a trial in which those choices were shown to be the optimal biological constants.

Skiba’s 2008 BikeScore methods note, a vendor document rather than a peer-reviewed trial, reconstructs Coggan’s method as a 30-second moving average plus a near-fourth-power weighting taken from a lactate-versus-percent-threshold curve. Skiba’s own xPower variant writes the steps out: smooth (he uses a 25-second exponentially weighted average instead of a 30-second moving average), raise to the fourth power, average, take the fourth root. GoldenCheetah’s glossary documents the same split: TSS-style NP uses a 30-second moving average; xPower uses a 25-second exponential smooth. On one illustrated file the two differed by a few watts (239 W versus 236 W). That is software agreement, not physiological validation.

CTL and ATL are exponentially weighted moving averages of daily TSS. TrainingPeaks states the product defaults directly: fatigue is an exponentially weighted average over a 7-day window, fitness over a 42-day window, and form is yesterday’s fitness minus yesterday’s fatigue. GoldenCheetah states the same defaults as time constants (typically 7 and 42 days) and is careful about the verb: these quantities are *claimed* to relate to fatigue, fitness, and form.

**Contradiction / limit.** None of these sources is a trial showing that the fourth-power exponent, the 30-second window, or the 42- and 7-day constants are the biological time constants of adaptation. When researchers fit impulse-response models, the time constants come out of the fit. They are not locked at 42 and 7 (Wallace, Slattery, and Coutts, 2014, in runners; Vermeire and colleagues, 2021, in a small cycling sample; Skiba, 2008, illustrative fit). See MON-C04.

**Practical implication.** Use TSS as a session diary that is comparable with itself only while the FTP setting is stable and honest. Never read a CTL integer as VO₂max, threshold power, or “form.”

**Uncertainty.** Platforms can implement the exponential weight as 1/τ or as 1 − e^(−1/τ). Those are close but not identical. The retrieved vendor pages confirm the 7- and 42-day defaults and the “yesterday minus yesterday” TSB rule; they do not publish the rounding convention.

<a id="mon-c02"></a>
### MON-C02 — Equal TSS is not equal stress, and a wrong FTP setting distorts the whole file

**Classification:** Strong evidence

**Claim.** Two rides with the same TSS can differ in mechanical work, intensity distribution, and internal cost. Because TSS scales with the square of IF when power is steady, the metric systematically down-weights long easy riding relative to kilojoules and up-weights variable or high-IF riding. An FTP set too high makes every subsequent TSS, IF, and zone look easier than the effort was.

**Support.** From the vendor formula, steady-state TSS = hours × IF² × 100. These are arithmetic consequences, not trial outcomes:

| Steady ride | IF | TSS | Mechanical work relative to 1 h at FTP |
|---|---:|---:|---:|
| 1.0 h at FTP | 1.00 | 100 | 1.0 |
| 2.0 h at 71% of FTP | 0.71 | 100 | 1.4 |
| 4.0 h at 50% of FTP | 0.50 | 100 | 2.0 |

Equal TSS, double the kilojoules, in the last row. The fourth-power step does the converse for variability: a criterium and a steady tempo with the same average power do not have the same NP, so they do not have the same TSS. Coggan’s explainer uses that as the point of NP. It still does not encode heat, altitude, low glycogen, sleep debt, illness, or residual fatigue from yesterday. Those change heart rate and session-RPE at the same power file.

van Erp, Foster, and de Koning (2019; 21 professional cyclists, 4 years, 11,655 sessions) found almost perfect correlations among kilojoules, session-RPE, Lucia TRIMP, and TSS in training, and very large to almost perfect correlations in races and time trials. The slopes were not the same. TSS collected in training versus road races differed by 120%, while kilojoules, session-RPE, and Lucia TRIMP differed by 73%, 67%, and 68%. A companion analysis (van Erp, Hoozemans, Foster, and de Koning, 2019) reported mean intensity factor 0.59 (SD 0.03) in training versus 0.73 (0.03) in races, and showed that the kilojoule–TSS association changes with IF, consistent with the quadratic IF term, whereas the kilojoule associations with session-RPE and Lucia TRIMP did not. Strong correlation is not interchangeability.

A wrong FTP is a scaling error, again from the formula rather than from a trial. If the entered FTP is 5% above the power the rider can actually sustain, every IF is divided by 1.05 and every TSS is multiplied by about 1/1.05², roughly a 9% understatement, before any change in how the rider actually rode. Zones prescribed from that FTP are also too high, so the session that the plan called “endurance” may have been tempo. Both errors hide stress. The opposite FTP error inflates TSS and makes prescribed endurance easier than the plan name suggests. Borszcz and colleagues (2018) showed why this is not a theoretical quibble: in 23 trained men, 95% of 20-minute power, 60-minute power, and the individual anaerobic threshold agreed on average (bias about −1 to −5 W) but the limits of agreement ran to tens of watts. An individual FTP setting can be systematically off while the group looks fine.

**Practical implication.** When comparing weeks, report hours and kilojoules beside TSS, and note whether the TSS came from long steady riding, intervals, or races. If FTP has not been checked recently, do not interpret a TSS or CTL change.

**Uncertainty.** The 9% figure is formula arithmetic for a steady file. A variable file moves by a similar proportion only if NP scales linearly with the FTP error, which it does, because FTP is not inside the NP calculation — it is only the divisor.

<a id="mon-c03"></a>
### MON-C03 — Hours, kilojoules, heart-rate load, and session-RPE answer different questions

**Classification:** Moderate evidence

**Claim.** Duration, mechanical work, a heart-rate impulse, and session-RPE are complementary descriptions. None is a sufficient summary of cycling stress, and none should be converted into another with a universal equation.

**Support.** Hours ignore intensity. Kilojoules are mechanical work (average power × time). They do not weight a minute at threshold above a minute of soft pedalling. Passfield and colleagues (2017) reviewed field power measurement and concluded that power meters can be accurate enough for training and racing analysis, but that a simple summary does not represent the distribution of power or the likely metabolic stress. Binning into zones keeps the intensity detail and loses the length of efforts. Their suggested alternative for monitoring change is the critical-power model or the record power profile, not a single load integer.

Heart-rate load tries to represent internal cost. Halson (2014) describes Banister’s training impulse as duration combined with resting, mean, and maximal heart rate, and notes later derivatives: Edwards’ TRIMP, time in five arbitrary heart-rate zones each multiplied by a zone weight, and Lucia’s TRIMP, three zones anchored to individually determined thresholds rather than fixed percentages of maximum heart rate. Lucia, Hoyos, and colleagues (2003) computed professional stage-race load that way: time below the ventilatory threshold, between that threshold and the respiratory compensation point, and above it, each multiplied by a phase weight and summed. The retrieved abstract does not state the integer weights, so they are not repeated here. Manzi and colleagues (2009) went further in eight recreational runners: an individualized TRIMP, weighted from each runner’s own heart-rate–lactate curve, tracked submaximal speed and 5 km / 10 km performance better than a group-average weighting. That was running, not cycling. Sanders and colleagues (2017) then compared methods in 15 well-trained road cyclists over 10 preseason weeks. Every method they tried (Banister, Edwards, individualized, and Lucia TRIMP, session-RPE, and TSS) had large to very large correlations (r = 0.54–0.81) with changes in power at 2 and 4 mmol/L. The strongest links to those fitness changes were individualized TRIMP and TSS. The strongest links to an 8-minute time trial were individualized TRIMP (r = 0.63) and Lucia TRIMP (r = 0.70), not TSS.

Session-RPE, as described by Foster and colleagues (2001) and restated in the GoldenCheetah glossary, is the post-session category-ratio rating multiplied by duration in minutes, typically collected about 30 minutes after the ride so the last interval does not dominate. Rodríguez-Marroyo, Villa, García-López, and Foster (2012) tested it in 12 professional cyclists (VO₂max 78.5 ± 1.7 mL/kg/min) across 5-, 7-, and 21-day races. Session-RPE load correlated with heart-rate TRIMP (r = 0.75; r = 0.90 when both were expressed per kilometre). Heart-rate load and perceptual load did not rank the race types identically until distance was accounted for. Foster, Rodríguez-Marroyo, and de Koning (2017) treat session-RPE as the practical descendant of Banister’s impulse: less laboratory calibration, fast enough for a coach, and still only one index.

Bossi, Matta, Lima, and Bara-Filho (2026) published a methodology review, not a multi-athlete trial, showing students how to calculate TSS, Edwards TRIMP, and session-RPE and how to compare them with regression and with partial correlation that removes the shared effect of duration. The worked data are one competitive cyclist. The retrieved abstract does not include the fit statistics, so those are not cited. The design point is the useful one: raw correlations between load metrics are inflated by duration, and a conversion fitted to one rider is not a general law.

Rothschild, Hofmeyr, McLaren, and Maunder (2025) showed a related boundary. In 15 cyclists (5 women; VO₂max 51.9 ± 7.2 mL/kg/min), within-subject correlations between several load metrics and both carbohydrate use and energy expenditure were very large to near perfect (r = 0.76–0.96). Prediction error grew in a separate validation sample until the model was recalibrated. Load scores can track exercise energy cost inside one person. They are still not a measured stress, and they are not a fueling prescription. Fueling belongs in its own topic.

**Contradiction / limit.** Vermeire and colleagues (2021) fitted the same fitness–fatigue model to Banister, Lucia, and Edwards TRIMP, TSS, session-RPE, and kilojoules in nine people doing three interval sessions a week for eight weeks, with performance checked by a weekly 3 km ergometer time trial. Prediction error was similar across inputs. The inputs were still not interchangeable: the day on which training had its largest positive influence differed by as much as 19.6 days depending on which load metric was used.

**Practical implication.** Log hours, kilojoules, and one internal score (session-RPE, plus heart rate if the trace is clean). Keep TSS if you already use it, but do not drop the others to “simplify to one number.”

**Uncertainty.** Most head-to-head cycling datasets are professional men (van Erp, Rodríguez-Marroyo) or small well-trained samples (Sanders, n = 15). Amateur women are thinly represented.

<a id="mon-c04"></a>
### MON-C04 — CTL and TSS are not validated enough to drive the plan by themselves

**Classification:** Moderate evidence

**Claim.** TSS and related impulses have dose–response associations with fitness changes in some observational blocks. That does not validate a CTL target, a ramp-rate rule, or the default 42- and 7-day constants as decision thresholds.

**Support.** Sanders and colleagues (2017) is the clearest cycling dose–response study in this set: 15 well-trained competitive cyclists, 10 weeks of preseason (December–March), laboratory lactate and gas exchange plus an 8-minute time trial. TSS correlated with changes in power at 2 and 4 mmol/L (r = 0.75 and 0.79). Individualized heart-rate TRIMP correlated at least as strongly, and heart-rate methods related more strongly to the performance trial. The study did not assign athletes to CTL targets. It observed that riders who accumulated more of several load scores tended to improve submaximal fitness. Causation, an optimal weekly TSS, and a safe CTL ramp are not in the result.

Wallace and colleagues (2014) are often cited for model validity and should be transferred cautiously. Seven trained runners (VO₂max 51.7 ± 4.5 mL/kg/min), 15 weeks, about a 5% improvement in 1,500 m. A Banister-type model of session-RPE, TRIMP, or a running TSS tracked weekly performance inside each runner (mean r about 0.60–0.70). The time constants were fitted, not taken from a software default. Runners are not cyclists, and n = 7 cannot set a population tau.

Vermeire and colleagues (2021) make the constant problem explicit in cycling-ergometer training: similar prediction error, different implied timing, depending on the load input. Skiba (2008) reported that TSS and his BikeScore fitted one illustrative performance series similarly, and that a crude TRIMP could do so too. His own example used fitted constants, not 42 and 7. A model that works about as well with kilojoules as with TSS (Vermeire) is a poor argument for letting the TSS-specific CTL number steer the week.

The IOC consensus statements (Soligard and colleagues, 2016, on injury; Schwellnus and colleagues, 2016, on illness) do support a broader claim: poorly managed load, including rapid changes, congested competition, psychological load, and travel, is associated with health risk. They do not validate a cycling CTL threshold. Halson (2014) likewise supports monitoring as a way to notice non-functional overreaching, not as a warrant for any one algorithm.

**Contradiction / limit.** TrainingPeaks publishes interpretive bands — TSS under 150 as generally recovered by the next day, form from slightly negative to about +25, and form as a clue to illness or injury (performance-management chart, updated 16 May 2026; Coggan TSS explainer). Those bands are product guidance. They are not outcomes of a controlled trial in trained cyclists.

**Practical implication.** Plan the week from available hours, the number of high-quality hard sessions that can be recovered, and the event, then use the load file to describe what was done. If CTL is falling because life removed three rides, the missing rides are the fact. The CTL drop is the echo.

**Uncertainty.** No retrieved trial randomized 7–12 h/week amateurs to “chase a CTL target” versus “progress recoverable, specific training and ignore CTL.” Absence of that trial is itself the limit on using CTL to drive decisions.

<a id="mon-c05"></a>
### MON-C05 — Acute:chronic ratios and TSB are not causal injury or readiness models

**Classification:** Strong evidence for the acute:chronic workload ratio; the same caution applies to TSB by construction

**Claim.** A ratio or difference between recent load and chronic load is a description of load timing. It is not a demonstrated cause of injury, and a TSB value is not a measurement of race readiness.

**Support.** Impellizzeri, Tenan, Kempton, Novak, and Coutts (2020) reviewed the acute:chronic workload ratio and concluded that its causal link to injury has not been established, that ratio statistics are misleading, and that there is no evidence base for using the ratio in load-management systems aimed at reducing injury. That literature is mostly team sport. It is cited here only to stop a common export: the idea that a cycling acute:chronic number, or a TSB threshold, is an injury switch. Windt and Gabbett (2019) had already flagged mathematical coupling in these ratios. This note does not build an injury-prediction system.

TSB, in the TrainingPeaks implementation, is yesterday’s CTL minus yesterday’s ATL. Negative TSB means the last week was heavy relative to the last month or so. That can be true of a productive overload and of a slump. Positive TSB means recent load is lower than the chronic average. That can be a taper, a holiday, or detraining. GoldenCheetah’s glossary states the claim-language honestly: TSB is *claimed* to relate to form or freshness.

**Practical implication.** Read TSB as “recent load versus usual load.” Decide freshness from sleep, session-RPE trend, wellness, and a standardized effort. Do not skip a key session because TSB crossed a published band, and do not add risk because TSB looks “positive.”

**Uncertainty.** Whether some other acute-versus-chronic summary, fitted per athlete, would predict illness in cyclists is not answered by the retrieved studies. The IOC statements support paying attention to spikes and to non-sport stress. They do not supply a cut-off.

<a id="mon-c06"></a>
### MON-C06 — Adaptation is judged from standardized performance, not from the load score

**Classification:** Strong evidence

**Claim.** The program is working if the performance you care about improves beyond the noise of the test, under conditions you can compare. A rising CTL is evidence that the diary got heavier. It is not evidence that VO₂max, threshold power, or fitness improved.

**Support.** This follows from the definitions in MON-C01 and from the measurement studies below. The sharpest empirical warning is Inglis, Iannetta, Passfield, and Murias (2020). Eighteen well-trained adults (12 men, 6 women) did ramp tests, lactate-steady-state trials, and a 20-minute field test. Ten returned after seven months of training. Power at maximal lactate steady state rose by 12 (8) W. Mean power in the 20-minute test, and 95% of that power, did not (P = 0.75). A load model fed by an unchanged FTP would have described the training. It would not have detected the steady-state change, and the field test itself missed it. Conversely, an athlete can accumulate TSS while ill, under-fueled, or overreached and post a higher CTL with worse power. Sanders (2017) shows association between load and improvement in a group that was training productively. It does not show that the load number is the outcome.

**Practical implication.** Keep a small set of repeatable efforts. Judge the block by those efforts and by whether key sessions are still completable at the planned power and perceived exertion. Use the load file to explain the result, not to replace it.

**Uncertainty.** “Beyond the noise” requires a personal or at least a protocol-specific error, which most amateurs do not have. Published typical errors are the best substitute and are summarized under Q21. They are not the athlete’s own error.

<a id="mon-c07"></a>
### MON-C07 — FTP, critical power, and a 3-minute all-out test are related, not interchangeable, and none is a VO₂max

**Classification:** Strong evidence

**Claim.** A 20-minute field test is reliable enough to track threshold-domain performance in trained cyclists. Ninety-five percent of that power is a coaching estimate of hour-power and of metabolic thresholds, with individual errors large enough to matter. Critical power from several maximal efforts is a better-defined heavy–severe boundary, but the number depends on the protocol. End-test power from a 3-minute all-out test is reliable and is not a validated shortcut to critical power or to W′. None of these tests measures VO₂max.

**Support.** Reliability first. Borszcz, Tramontin, and Costa (2020): 25 trained cyclists, familiarization plus two tests a week apart, Allen and Coggan 20-minute protocol. The 20-minute result was reliable (CV 2.9%, ICC 0.97). The elaborate warm-up was less so (CV 5.5%). MacInnis, Thomas, and Phillips (2019): eight trained men (VO₂max 71 ± 5 mL/kg/min). Typical error 8.1 W (ICC 0.98) for repeated 4-minute trials and 4.6 W (ICC 0.99) for 20-minute trials. Critical power estimated from the 4- and 20-minute pair had typical error 6.5 W. All three related strongly to the single 60-minute mean power (309 ± 26 W). Lillo-Beviá and colleagues (2022): 11 trained men (VO₂max 59.7 ± 3.0 mL/kg/min), laboratory 20-minute tests, standard error of measurement ±3 W, smallest detectable change ±9 W. A change smaller than that is not a training effect.

Validity against physiological anchors is only moderate, and the papers disagree on the mean while agreeing on the spread. Borszcz and colleagues (2018, n = 23 trained men): 95% of 20-minute power, 60-minute power, and the individual anaerobic threshold were not different on average, correlations 0.61–0.88, bias a few watts, limits of agreement from about ±30–40 W to about ±60 W. Time to exhaustion at the 20-minute estimate was 50.9 ± 15.7 min, not 60. Borszcz, Tramontin, and Costa (2019, n = 15, VO₂max 62.3 ± 6.4 mL/kg/min) found FTP within 1.4% ± 9.2% of maximal lactate steady state (typical error of the estimate 4.7%, r = 0.91), tighter in the well-trained subgroup (3.0%) than in the trained subgroup (6.4%). They called FTP a practical alternative. The limits of agreement still span roughly ±9% for an individual. Valenzuela, Morales, Foster, Lucía, and de la Villa (2018, n = 20 men) found FTP and a lactate threshold strongly correlated (r = 0.95) and not different overall (limits of agreement −2.4% ± 11.5%), but the bias depended on fitness: acceptable in trained cyclists, prone to underestimate the lactate threshold in recreational cyclists. Sitko, Cirer-Sastre, and López-Laval (2022) reported median time to exhaustion at the Allen and Coggan FTP of 35 minutes in recreationally trained cyclists, 42 in trained, 47 in well-trained, and 51 in professional-level cyclists. The retrieved abstract does not state the sample size. The direction is clear: the hour-power story is worst in the riders least like the professionals the heuristic was built around. Sitko and colleagues (2022, n = 46, VO₂max 61.1 ± 9.1 mL/kg/min) also found large correlations with some lactate landmarks (r = 0.68–0.93) and significant differences from others. Mackey and Horner’s scoping review (2021, 15 studies) summarized the field the same way: FTP20 is reported as reliable; limits of agreement are too wide for interchange with other markers; samples are mostly trained men; physiological justification is still thin.

Inglis and colleagues (2020) are the hostile result: maximal lactate steady state was 88.5% (4.8%) of 20-minute power and 93.1% (5.1%) of the 95% estimate, and the field test missed a 12 W steady-state gain. Lillo-Beviá and colleagues found a 26 ± 7 W gap from the raw 20-minute power to steady state, and 12 ± 7 W remaining after the traditional 95% factor. An in-sample factor near 91%, and an in-sample regression, shrank the bias. Those corrections were fit on the same 11 riders. They are not a new universal constant.

Critical power is the more coherent physiological object — a heavy–severe boundary, not a 60-minute average — but it is not protocol-proof. Karsten and colleagues (2021): 17 trained cyclists and triathletes (VO₂peak 51 ± 10 mL/kg/min), single-visit 12-, 7-, and 3-minute tests versus 95% of 20-minute power. Correlation 0.969, mean bias 7 ± 13 W, limits of agreement −19 to 33 W, with critical power likely higher. Karsten, Jobson, and colleagues (2015) found field critical power could be reliable (CV 2.4% when 12-, 7-, and 3-minute efforts were done in one session with 30 minutes of recovery; 6.5% when efforts were separated; 3.5% when taken from training and racing peaks) and still showed wide limits of agreement against laboratory critical power. Habets, de Jong, and colleagues (2026): 12 highly trained professional men, modelled maximal lactate steady state 357 ± 30.6 W versus critical power estimated from 3- and 20-minute maximal mean powers 364 ± 21.5 W (r = 0.881). Group agreement, substantial individual scatter. The authors argue against treating the two constructs as the same thing. Bartram, Thewlis, Martin, and Norton (2017): six elite track endurance riders, 3-minute all-out end-test power 402 ± 33 W versus traditional multi-effort critical power 351 ± 27 W. Not interchangeable in that group.

Quittmann and Piehl (2026; systematic review and meta-analysis, search 20 June 2025, 20 cycling studies, N = 284, samples mostly n = 6–21 and mostly male) is the current summary of the 3-minute shortcut. Test–retest reliability of end-test power was good to excellent (ICC 0.89–0.99) and of work above end-test power good to excellent but wider (ICC 0.76–0.98), provided retests fell within about three weeks and riders were familiarized. Validity was heterogeneous. Random-effects pooling found end-test power systematically overestimated critical power (Hedges’ g_z = 0.408, 95% prediction interval 0.024 to 0.792) and work above end-test power underestimated W′ (g_z = −0.389, prediction interval −0.954 to 0.176). In pooled individual data (Results, Figure 2), end-test power correlated almost perfectly with critical power (r = 0.993) with a standard error of the estimate of 21 W, mean difference +11.7 W, and limits of agreement −37.1 to +60.5 W. Agreement between 3-minute work above end-test power and traditionally modelled W′ was poor (r = 0.499, SEE 5.4 kJ, mean difference −3.0 kJ, limits of agreement −14.1 to +8.0 kJ). Those kilojoule figures are cross-method disagreement, not the repeatability or smallest detectable change of a fitted multi-effort W′. The review does not establish a 2 kJ decision threshold for longitudinal W′. The authors advise against estimating W′ from the 3-minute test. Familiarization and real verbal encouragement are mandatory. Wright, Bruce-Low, and Jobson (2017), included in that review, illustrate the split inside one sample of 12 riders: end-test power CV about 1–2%, work-above-end-test-power CV about 5–8%, and neither matched the traditional W′.

Denham, Scott-Hamilton, Hagstrom, and Gray (2020) reported that cycling power outputs predict FTP and VO₂max in a heterogeneous cohort. That is a group association. It is not a measurement of oxygen uptake. Software that estimates VO₂max from a few minutes of power (GoldenCheetah documents one such ACSM-style conversion) is producing a prediction, not a laboratory value. Do not enter an FTP gain in a log as a VO₂max gain.

**Practical implication.** Pick one protocol and keep it: either a familiarized 20-minute test, or two or three maximal efforts spread between about 3 and 20 minutes for a critical-power estimate. Repeat it fresh, on the same equipment, every block — not every week. Do not replace it with a 3-minute all-out test if the question is critical power or W′. Do not convert the result to VO₂max.

**Uncertainty.** The best agreement papers and the hostile papers used different threshold definitions (individual anaerobic threshold, Dmax-type lactate landmarks, maximal lactate steady state, ventilatory thresholds). Some of the conflict is the anchor, not the field test. Sex-specific error is largely unmeasured.

<a id="mon-c08"></a>
### MON-C08 — Submaximal heart rate, decoupling, resting heart rate, and HRV are trend tools, not day-pass tests

**Classification:** Moderate evidence that the signals exist and are noisy; the common 5% decoupling rule is mostly coaching practice

**Claim.** A fall in heart rate at a truly standardized power, over weeks, is a useful aerobic trend. A single ride’s decoupling percentage, a single morning heart rate, or a single HRV value is usually inside the noise, and is confounded by heat, fluid, fuel, caffeine, and sleep. A 5% decoupling cut-off is not a validated pass/fail for aerobic fitness.

**Support.** Cardiovascular drift is a real phenomenon with several causes. Montain and Coyle (1992) showed graded dehydration amplifying hyperthermia and drift. Coyle and González-Alonso (2001) reviewed drift in prolonged exercise as more than a trivial heart-rate rise: stroke volume falls and, in the heat, the drift is tied to a lower VO₂max (Wingo and colleagues, 2005, title result). Friel’s TrainingPeaks article (first published 2008, updated 3 June 2026) lists the same cluster — core temperature, dehydration, glycogen, cardiovascular fatigue — and then offers coaching bands for the software metric that compares the first half of a steady effort with the second half: under 5% “strong aerobic endurance,” 5–10% moderate limitation or fatigue, over 10% too hard or under-prepared. The same article says there is no hard research-based rule for how long a cyclist should stay coupled. GoldenCheetah’s glossary repeats the 5% heuristic and immediately qualifies it: excessive decoupling can indicate weak aerobic endurance and is also affected by heat and dehydration. The 5% rule is therefore a coaching convention published by the vendor, not a trial endpoint.

Rothschild and colleagues (2025; 51 trained cyclists, durability of power at the first ventilatory threshold across about 2.5 hours) is a different claim and should not be merged with Friel’s rule. Heart-rate and respiratory decoupling during controlled prolonged cycling tracked the downward drift of threshold power, and a multivariable model predicted concurrent threshold power with a mean absolute error around 7 W in that dataset. That supports decoupling as a *within-ride durability* marker under laboratory-like control. It does not validate a 5% pass/fail on an ordinary outdoor endurance ride, and it does not show that a low decoupling percentage caused a later fitness gain.

Buchheit (2014) quantified why morning numbers fail as daily switches. In his summary table, resting heart rate had a typical error near 10% against a smallest worthwhile change near 2% (signal-to-noise about 0.7). Vagal HRV indices were index-dependent; ln rMSSD was near 12% typical error against a smallest worthwhile change near 3%. Exercise heart rate was cleaner (typical error near 3%, signal-to-noise about 1.6) and still not a one-day verdict. Plews, Laursen, Stanley, Kilding, and Buchheit (2013) showed that elite endurance athletes do not follow the simple story “HRV up means adapting, HRV down means failing.” Highly fit athletes can show HRV saturation: vagal indices fall even as resting heart rate falls and fitness rises. They recommended individual rolling averages and an individual fingerprint, not a population cut-off.

**Practical implication.** Embed a short steady segment (same power, similar temperature, similar fuel, similar caffeine) in an easy ride every week or two. Plot heart rate at that power, and power at a fixed heart rate, as 2–4 week trends. Ignore a 5% decoupling flag unless the ride was controlled and the pattern repeats. Average resting heart rate and ln rMSSD over about seven days before you even describe the trend. Do not cancel or add a key session on one morning value.

**Uncertainty.** How much of a multi-week drop in submaximal heart rate is plasma volume, how much is mitochondrial or efficiency change, and how much is heat acclimation is not separable from a power-and-heart-rate file alone. The trend can be real and still be the wrong adaptation for the goal.

<a id="mon-c09"></a>
### MON-C09 — Wellness often moves before objective markers; HRV-guided training is optional, not superior by default

**Classification:** Moderate evidence

**Claim.** A short subjective check (sleep, fatigue, soreness, stress or mood, session-RPE) is one of the more sensitive ways to see that load is or is not being absorbed. Guiding the day’s intensity from HRV has a plausible rationale and small average performance effects. Combining HRV with resting heart rate and wellness is more defensible than HRV alone. It is not a proven upgrade over a well-built fixed plan for VO₂max or threshold power.

**Support.** Saw, Main, and Gastin (2016) systematically reviewed studies that collected both subjective and objective athlete-monitoring measures. Subjective self-reports were more sensitive and consistent than the objective measures in 22 of 54 studies. Objective markers, including many resting physiological and blood measures, were generally unresponsive to acute load changes. The review is not cycling-specific, and many included studies were small. It is still the best evidence that a four-item wellness score is not a soft substitute for “real” monitoring. It is often the more responsive instrument. Kellmann and colleagues (2018) and Meeusen and colleagues (2013) place the same idea in consensus language: recovery is multidimensional, and overtraining is a clinical diagnosis, not a single heart-rate or load cut-off. Those two statements were identified and not re-extracted in full; they are cited for that scope, not for marker thresholds.

HRV-guided training has two similar meta-analyses. Manresa-Rocamora and colleagues (2021; search to October 2020) found HRV-guided training better than predefined training for vagal HRV indices (SMD 0.50, 95% CI 0.09 to 0.91) and not for resting heart rate (SMD 0.04). Effects on maximal aerobic capacity (SMD 0.20, −0.07 to 0.47), capacity at the second ventilatory threshold (SMD 0.26, −0.05 to 0.57), and endurance performance (SMD 0.20, −0.09 to 0.48) favoured HRV guidance but were small and not significant. Düking and colleagues (2021; 8 studies, 198 participants, 9 interventions, search March 2020) found a medium effect on submaximal physiological parameters (g = 0.296, 0.031 to 0.562) and small non-significant effects on performance (g = 0.079) and VO₂peak (g = 0.171). HRV-guided arms often did fewer moderate or hard sessions and had fewer non-responders. Samples mixed sports and training status. A 2026 SWOT perspective (Schaffarczyk and Sperlich) does not add a new pooled effect. It argues that the limiting problem is no longer collecting HRV, but the opaque rules that turn a morning number into a session.

Cyclist trials are few. Javaloyes, Sarabia, Lamberts, and Moya-Ramón (2019): 17 well-trained cyclists, 4 baseline weeks then 8 training weeks. The HRV-guided group improved peak power (5.1% ± 4.5%), power at the second ventilatory threshold (13.9% ± 8.8%), and a 40-minute time trial (7.3% ± 4.5%). The traditional group did not improve significantly. Between-group differences were not significant; magnitude-based inference called the time-trial contrast “likely beneficial.” Vesterinen and colleagues (2016) is the cleaner design in recreational runners, not cyclists: HRV guidance produced fewer hard sessions (13.2 ± 6.0 versus 17.7 ± 2.5) and a 2.1% versus 1.1% gain in 3,000 m, a small between-group difference, with VO₂max up in both. Alfonso, Clarke, and Capdevila (2025): 28 experienced male cyclists, 40 days, three readiness rules and no predefined-plan control. All groups improved 1-, 5-, and 20-minute power and FTP. The group using vagal HRV plus wellness plus resting heart rate improved most (5-minute power 310.5 ± 60 to 337.9 ± 71 W; 20-minute power 260.9 ± 55 to 284.5 ± 64 W). Individual correlations between the markers were heterogeneous. Perceived stress was the most consistent subjective item from day to day. That supports a composite. It does not show that the composite beat a sensible fixed plan.

**Practical implication.** Keep the wellness score and session-RPE whether or not you own an HRV app. If you use morning HRV, use a rolling baseline and a written rule, and let wellness and resting heart rate veto a “green” HRV day that does not feel green. Do not expect the app to raise VO₂max more than a plan that already has two hard sessions and enough easy riding.

**Uncertainty.** Publication bias and short interventions (often ≤8 weeks) are explicit concerns in the meta-analyses. Almost all cyclist HRV trials are small and male.

<a id="mon-c10"></a>
### MON-C10 — When the numbers conflict, trust the repeated performance test and the internal response over the smoothed external score

**Classification:** Moderate evidence for the priority rule; the exact checklist is a practical synthesis, not a trial

**Claim.** If CTL says one thing and a standardized performance test plus session-RPE and wellness say another, believe the test and the internal response. The external score is an input log.

**Support.** This is the decision rule implied by MON-C01 through MON-C09, not a separate experiment. van Erp’s slope differences, Inglis’s missed steady-state change, Buchheit’s signal-to-noise ratios, Saw’s subjective-versus-objective review, and Impellizzeri’s rejection of acute:chronic injury switches all point the same way. The week-by-week procedure in [the workflow](#conflict-resolution-workflow) is coaching assembly of those findings. It has not been tested as a package against usual care.

**Practical implication.** Write the conflict down in one line (“CTL up, 20-minute power flat, session-RPE up, sleep down”) and apply the priority rule. Do not average the contradictions into a new CTL target.

**Uncertainty.** An athlete with no performance test and a noisy wellness habit has nothing reliable to put above CTL. The fix is to install the test and the habit, not to trust CTL more.

---

<a id="q20-training-load-metrics"></a>
## Q20. Training-load metrics

### What each metric is

| Metric | What is actually computed | Source of the formula | What it is not |
|---|---|---|---|
| Hours | Elapsed riding time | Clock | Intensity, stress, or adaptation |
| Kilojoules | Mechanical work: mean power × duration | Physics of the power file | A weighted stress score. Two platforms can disagree if the file is processed differently; that processing rule was not re-verified here |
| Normalized power | Variable power restated as an equivalent steady power. Coggan’s version, as reconstructed by Skiba (2008) and implemented in GoldenCheetah: 30-second moving average, then a fourth-power weighting. Skiba’s xPower uses a 25-second exponential smooth and the same fourth-power steps | Vendor / software. The fourth power is motivated by a lactate-versus-intensity curve, not fit as an athlete’s biological exponent | Valid for very short efforts (GoldenCheetah says to use average power instead). Not glycogen use, not muscle damage, not heat stress |
| Intensity factor | NP / FTP | Coggan, TrainingPeaks, updated 2026 | A fraction of VO₂max or of lactate threshold, unless FTP happens to match that anchor |
| TSS | (seconds × NP × IF) / (FTP × 3600) × 100. One hour at the entered FTP = 100 | Friel / TrainingPeaks, formula page updated 2026; described as modelled on Banister’s impulse | Biological equivalence between sessions. A heart-rate analogue that scores about 100 for an hour at threshold heart rate exists in some software (GoldenCheetah’s TRIMP-100). Same construction, different input |
| CTL | Exponentially weighted moving average of daily TSS, default time constant 42 days | TrainingPeaks and GoldenCheetah product conventions | Fitness, VO₂max, or a target copied from another athlete |
| ATL | Same average with a default 7-day constant | Same | “Fatigue” as a sensation or a performance decrement |
| TSB | Yesterday’s CTL minus yesterday’s ATL | TrainingPeaks | Freshness, illness risk, or a taper prescription |
| Banister TRIMP | Duration × a heart-rate-reserve fraction × an exponential intensity weight | Halson (2014) describes the structure; the 1991 chapter and the often-quoted sex-specific coefficients were not retrieved, so the coefficients are not stated | A power-file quantity. Heart rate must be trustworthy |
| Edwards TRIMP | Minutes in five arbitrary heart-rate zones, each times a zone weight | Edwards, via Halson (2014). Exact zone boundaries were not in the retrieved text | Individually anchored thresholds |
| Lucia TRIMP | Minutes in three zones bounded by ventilatory threshold and respiratory compensation point, each times a phase weight, summed | Lucia and colleagues (2003); Halson (2014). Integer weights not in the retrieved abstract | Interchangeable with TSS. van Erp showed the slopes differ |
| Individualized TRIMP | Weighting taken from the athlete’s own heart-rate–lactate curve | Manzi and colleagues (2009), runners; used by Sanders and colleagues (2017) in cyclists | Practical for weekly amateur use unless the lactate curve exists |
| Session-RPE | Category-ratio RPE about 30 minutes after the ride × minutes | Foster and colleagues (2001), as cited in secondary descriptions; cyclist correlation data in Rodríguez-Marroyo and colleagues (2012) | Immune to expectation, peer effects, or a misunderstood scale. It is still the cheapest internal load |

Bossi and colleagues (2026) are the latest methods paper in this set: a tutorial on computing TSS, Edwards TRIMP, and session-RPE, comparing them with and without the confounding effect of duration, in one competitive cyclist. Treat it as a calculation guide. Do not treat a regression from that case study as your conversion formula. The fit numbers were not in the retrieved abstract.

### Why the fourth power and the 42-day constant feel more biological than they are

Coggan’s rationale is physiologically motivated. Lactate, catecholamines, and glycogen use do rise nonlinearly as intensity approaches and passes threshold, and heart rate, ventilation, and plasma epinephrine do not jump in a single second when power does. A 30-second smooth and a steep intensity weight are reasonable engineering choices. Skiba (2008) already noted the weakness: physiological decay is exponential, so a rectangular 30-second window is itself a compromise, which is why he tried a 25-second exponential smooth. On the files he plotted, NP and xPower barely differed. Changing the window did not create a new physiology. Changing the exponent would change TSS, and nobody has shown that 4.0 outperforms 3.5 or 4.5 for predicting the next block of adaptation in trained cyclists.

The 42- and 7-day constants have the same status. They are round numbers in the neighbourhood of “fitness changes over weeks, fatigue over days,” which is true and not specific. A time constant of 42 days means a day six weeks ago still carries weight, and the half-life of the average is about 0.69 × 42 days, not 42. TrainingPeaks’ plain-language “average of the last 42 days” is therefore a description of the window, not a simple moving average. Vermeire’s result — the most influential day shifting by up to about three weeks when the load input changed — is what “the constant is not biological tau” looks like in data.

### Heart-rate load, drift, and the amateur without a power meter

Heart rate is the internal record power cannot see. It is also late, capped, and dirty. It lags changes in power by tens of seconds, which is one reason NP was invented (Skiba, 2008; Coggan explainer). It drifts upward in the heat and with dehydration even if fitness is unchanged (Montain and Coyle, 1992; Coyle and González-Alonso, 2001; Wingo and colleagues, 2005). Caffeine, stimulants, fever, and poor sleep move it. A TRIMP computed from a drifted file will call the second hour harder than the first even when power was flat. That can be the right internal description and the wrong conclusion about aerobic base. See Q21 on decoupling.

For a rider with no power meter, hours plus session-RPE is a complete enough external-plus-internal pair. A heart-rate TRIMP adds information on days when the strap worked and the ride was not a stop-start commute. Inventing TSS from an RPE table, as Friel’s estimation article allows, is bookkeeping so the performance-management chart is not blank. It inherits every limitation of TSS and adds the error of the estimate. Do not compare that estimated CTL with a friend who has a power meter.

### 7–12 hours versus 20–30 hours

Professional files are a poor template for an amateur CTL target. van Erp, Sanders, and de Koning (2020) described four years of training in 20 male and 10 female professionals. Men accumulated more distance, duration, and kilojoules, and rode at a higher mean power (standardized effects 0.44–1.98). TSS and TRIMP differed only trivially between the men and the women (effects 0.07–0.12); the women carried more load per kilometre. Absolute weekly hours were not in the retrieved abstract, so they are not stated. The user’s 20–30 hour frame is the comparison of interest, not a result of that study.

What does transfer:

- The metrics behave the same way. van Erp’s quadratic TSS effect (training IF near 0.59, race IF near 0.73, TSS exaggerating the gap) will appear in an amateur criterium versus an amateur endurance week. Equal weekly TSS can hide a completely different intensity distribution.
- The absolute numbers do not transfer. A professional’s sustainable TSS is the product of a high FTP, a large easy-volume base, and a life organized around recovery. An amateur who imports the CTL will usually import the hard part and skip the easy hours that made the professional’s IF low. Session-RPE and wellness will show the mismatch before CTL does, because life stress is inside the perceptual score and outside the power file.
- At 7–12 hours, the diary is short. Two missed rides move CTL more, in relative terms, than two missed rides in a 25-hour week, and each hard session is a larger fraction of the adaptive stimulus. The highest-value monitoring act is not a smoother model. It is knowing whether those one or two hard sessions were completed at the intended power and perceived exertion, and whether the easy rides stayed easy enough to allow the next one.
- Retest less often than a professional service might, not more. A maximal test costs one of the few high-quality days. Every 6–8 weeks, or at the end of a block, is enough given a 20-minute CV near 3% (Borszcz, 2020). Pros can bury a test inside a large week. Amateurs should not.

What does not transfer: ramp-rate rules of thumb, “optimal” CTL for a category, and the idea that a 30-hour rider’s low decoupling on long rides is the standard an 8-hour rider should pass before doing VO₂ work. Decoupling on a 4-hour ride is a durability question. An amateur whose event is 60–90 minutes needs a durable aerobic base, not a professional long-ride screen. Durability as a trainable quality is the other topic. The monitoring point is only: do not use a fresh FTP test and a fatigued long-ride effort as the same outcome.

### Is there a minimum useful set?

Yes. Hours, session-RPE, and a note of whether the planned session happened. Add kilojoules if a power meter exists. Add TSS only if FTP is current. Add heart rate on steady rides if you will actually look at the trend. That set answers Q20 without a performance-management chart. The chart is optional annotation.

---

<a id="q21-monitoring-adaptation"></a>
## Q21. Monitoring adaptation

### What “working” means

For this athlete, working means one or more of the following, beyond test noise, over a block of several weeks: higher power at a repeatable threshold-domain test (20-minute mean or critical power), higher power in the 4–5 minute domain if VO₂max-oriented work was the emphasis, and the ability to do the planned hard sessions without a rising session-RPE trend or a falling wellness trend. A lower heart rate at the same standardized power is supporting evidence of cardiovascular adaptation, not proof by itself. A higher CTL is not on the list.

VO₂max itself is not on the home list unless it is measured. FTP and 5-minute power correlate with VO₂max in groups (Denham and colleagues, 2020; MacInnis and colleagues, 2019, for the association of short trials with 60-minute power, not with oxygen uptake). Correlation is not a test of oxygen uptake. If the goal is VO₂max, either measure it occasionally in a laboratory or accept a field proxy and call it a proxy: power in a maximal 4–5 minute effort, or peak power in a ramp, under the same protocol. Do not back-calculate millilitres.

### Performance tests: what to keep, what to ignore

**20-minute power / FTP.** Best single field test in the retrieved set for repeatability (CV 2.9% in 25 trained cyclists; typical error 4.6 W in eight very fit men; laboratory SEM 3 W and smallest detectable change 9 W in 11 trained men). Use the 20-minute mean itself as the longitudinal outcome. Apply 95% only if you need a zone anchor, and expect individual error of several percent against lactate steady state, worse if you are recreational rather than well trained (Valenzuela, 2018; Borszcz, 2019; Inglis, 2020). Do not expect to hold that anchor for an hour. Time-to-exhaustion data say about 35–50 minutes for non-professionals (Sitko, 2022; Borszcz, 2018). Update zones when the 20-minute mean changes by more than the smallest detectable change you are willing to believe — on the order of 3% or about 10 W, not 2 W.

**Critical power and W′.** Prefer two or three maximal efforts between about 3 and 12–20 minutes, same protocol each block, if you want a heavy–severe boundary rather than a 20-minute score (Karsten, 2015, 2021; Habets, 2026). Field CV can be about 2–7% depending on whether efforts are same-day, separate days, or scraped from races. That CV is for critical power, not a W′ retest error. Three-minute work above end-test power is a poor substitute for W′ (Quittmann and Piehl, 2026, Figure 2: cross-method SEE 5.4 kJ, limits of agreement −14.1 to +8.0 kJ versus traditionally modelled W′). Longitudinal multi-effort W′ changes need protocol-specific repeatability. That review does not establish a 2 kJ decision threshold. Do not treat W′ as a fuel tank that empties in kilojoules you can read off the head unit; the modelling papers treat it as a curvature constant with protocol dependence, not as a measured anaerobic store.

**3-minute all-out.** A reliable hard effort (end-test power ICC often above 0.90) and a biased estimate of critical power, especially if you care about trained and elite riders (Bartram, 2017; Quittmann and Piehl, 2026). Familiarize first. Do not use the work-above-end-test-power number as W′.

**5-minute and 4-minute power.** Useful outcome for VO₂-oriented blocks because the intensity domain is closer to the stimulus than a 20-minute test is. MacInnis and colleagues’ 4-minute typical error was 8.1 W in a tiny sample of very fit men. One heroic 5-minute effort on a tired Thursday is not a VO₂max test and not a trend. Keep it inside the same fresh protocol as the 20-minute or critical-power test.

**Power-duration curve.** Passfield and colleagues (2017) argue that the curve, or the record power profile, is a better longitudinal picture than a session summary. That is right, with two conditions. Compare like with like: fresh curve versus fresh curve, or a curve built from the same set of efforts. A best-of file that silently includes a tailwind, a draft, or a fatigued race effort will “improve” without a fitness change. And do not read each duration as a separate biological system. Four-minute power, 20-minute power, and critical power overlap. A gain in one without the others is often pacing, fuel, or noise.

### Fresh versus fatigued

These answer different questions and must not be trended on the same plot.

**Ceiling test (did FTP, critical power, or 4–5 minute power change?):** at least one easy day before; same time of day; same ergometer or the same calibrated power meter; same warm-up; similar carbohydrate and caffeine; indoor, or the same outdoor course in similar weather; stop the test if illness or clearly abnormal wellness says the day is not a test day. Record those conditions in the note. Inglis and colleagues show that even a careful fresh FTP test can miss a lactate-steady-state change, so do not expect one protocol to capture every adaptation. It will at least be comparable with itself.

**Durability check (can you still produce power after a long ride?):** a separate session, with a fixed preload — same duration or same kilojoules at a fixed fraction of the current anchor — then the same effort you use when fresh. The difference between fresh and preloaded power is the durability observation. It is not an FTP update. Quittmann and Piehl note that a 3-minute all-out test can remain reliable after a standardized two-hour heavy ride (Clark and colleagues, 2018, as cited there). Reliability after fatigue is not permission to mix the numbers with rested tests. How durability is trained is outside this note.

### Heart rate at fixed power, power at fixed heart rate, decoupling

Use both heart-rate views, and do not let either become a 5% tribunal.

- **Heart rate at fixed power** falling over several controlled repeats is consistent with more plasma volume, better thermoregulation, or a truly easier relative intensity. It is also consistent with more rest, cooler weather, or more caffeine abstinence. Hold those constant before you call it fitness.
- **Power at fixed heart rate** rising is the same phenomenon from the other side, and it is what riders notice when they “used to sit at 140 beats and now sit at 150 watts more.” It is only interpretable if the heart-rate target is below the point where drift and cardiac lag dominate, and if the segment is long enough for heart rate to stabilize (several minutes, not 30 seconds).
- **Decoupling** (first half versus second half of a steady effort) mixes fitness, fuel, heat, and duration. Friel’s bands (<5%, 5–10%, >10%) are coaching practice. GoldenCheetah already warns about heat and dehydration. Rothschild and colleagues (2025) support a controlled version of the idea for tracking the drift of the first ventilatory threshold during a long ride. That is a durability measurement under standard conditions, not a licence to fail an athlete whose Tuesday endurance ride was 28 °C and under-fueled.

A practical rule that stays inside the evidence: do not change the plan because one ride decoupled by 5–8%. Do change the plan, or at least the fueling and the intensity of easy rides, if controlled repeats over a month show rising heart rate at the same power and the performance test is flat. The combination is the information. The percentage is not.

### Resting heart rate and HRV

Collect them if the ritual is easy. Interpret them as a weekly mean.

Buchheit’s (2014) error table is the reason. A smallest worthwhile change of about 2% in resting heart rate against a typical error near 10% means a bad morning is the default, not a diagnosis. ln rMSSD is similar (typical error near 12%, worthwhile change near 3%). Plews and colleagues (2013) add the elite-athlete trap: a falling HRV can be saturation, not failure, and the only defence is the athlete’s own history plus resting heart rate. Alfonso and colleagues (2025) found that, in experienced male cyclists, the relationships between vagal HRV, resting heart rate, and wellness items were individual. Stress ratings were more consistent day to day than the other subjective items. A group rule of the form “ln rMSSD down 8 milliseconds means rest” will be wrong for a large minority.

Recent interventions do not justify a tighter rule. The 2021 meta-analyses (Manresa-Rocamora; Düking) show a real effect on vagal HRV and a small, often non-significant effect on performance and VO₂peak, sometimes with fewer non-responders and fewer hard sessions. Javaloyes (2019) is encouraging and underpowered for a between-group claim. Alfonso (2025) supports adding wellness and resting heart rate to HRV and does not include a fixed-plan control. Schaffarczyk and Sperlich (2026) are right that the missing piece is a transparent decision rule, not another sensor. Until that exists, the defensible amateur rule is: seven-day baseline, change the day only when HRV, resting heart rate, and wellness agree, and never add intensity on a single good morning after a heavy week.

### Sleep, fatigue, soreness, RPE, and the session itself

Saw and colleagues (2016) justify a daily four- or five-item check more than they justify another physiological toy. Use the same items in the same order: sleep quality, fatigue, muscle soreness, stress or mood, and optionally motivation. Session-RPE after every ride, including the easy ones. The comparison that matters is session-RPE for the same planned session across weeks. A VO₂ session that used to be a 7 and is now a 9, at the same power, is a load or recovery problem even if TSS is unchanged.

The session is also a test. If the plan called for five four-minute efforts and the fifth effort collapsed, that is training-performance data. It is more specific than CTL and noisier than a rested time trial. Log it. Do not “correct” it by raising FTP because one interval felt good, or by slashing the week because one interval fell apart after a bad night.

### Composite, not a dashboard

Halson (2014): no single marker is definitive. Bourdon and colleagues (2017): monitoring is multidisciplinary or it is theatre. The composite that matches the evidence is small:

1. External diary — hours, kilojoules, and TSS only as a footnote tied to a current FTP.
2. Internal diary — session-RPE every ride; heart rate on steady work if the trace is clean.
3. Response — daily wellness; optional seven-day resting heart rate and ln rMSSD.
4. Outcome — one fresh performance protocol per block; key-session completion as the interim check.

Anything else (W′, daily TSB, a decoupling percentage, a predicted VO₂max) is optional annotation. It does not get a vote equal to the four lines above.

<a id="metric-comparison-table"></a>
### Metric comparison table

Costs assume a rider who already owns a bicycle. “Noise” is the decision noise, not the sensor specification. Cadence is for a 7–12 h/week amateur, not a professional service.

| Metric | Cost | Use it for | Noise / error | Review cadence | Coaching note |
|---|---|---|---|---|---|
| Hours | None | Volume, life fit | Low | Weekly | Necessary and not sufficient |
| Kilojoules | Power meter | Mechanical work | Device and file processing | Weekly | Compare with TSS; a gap means intensity, not a mystery |
| NP, IF, TSS | Power meter + current FTP | Relative external dose | Moves about 2% in TSS for each 1% FTP error, from the formula; also spikes and zeros | Weekly bookkeeping | Not stress. Not comparable across a stale FTP |
| CTL, ATL, TSB | Derived | “Heavier or lighter than my recent usual” | Smooth, therefore late | Glance weekly | Never a target. Vendor 42/7 are conventions |
| Session-RPE | 15 seconds | Internal cost | Depends on a stable personal scale | Every ride | Best cheap cross-check on TSS |
| Heart-rate TRIMP | Strap | Internal cardiovascular load | Drift, heat, caffeine, dropouts | Rides with a clean trace | Different slope from TSS in pros (van Erp, 2019) |
| 20-min power / FTP protocol | One hard session and an easy day | Threshold-domain change | CV ~3% trained (Borszcz, 2020); lab smallest detectable change ~9 W (Lillo-Beviá, 2022) | Every 6–8 weeks, fresh | Track the 20-min mean. 95% is a zone estimate, not hour power |
| 4–5 min power | Same test session | High-intensity outcome | TEM 8 W on 4 min in 8 very fit men (MacInnis, 2019) | With the block test | Not a VO₂max |
| Critical power, multi-effort | Two or three hard efforts | Heavy–severe boundary | Field CV ~2–7% by protocol (Karsten, 2015); individual gap vs FTP often tens of watts | Every 6–8 weeks, same efforts | Do not mix models between tests |
| 3-min all-out | One hard effort after familiarization | A repeatable hard number | End-test power reliable; bias vs critical power systematic (Quittmann, 2026) | Not as the CP test | Do not read W′ from it |
| W′ | From a repeated multi-effort model | Curvature constant, not a weekly steering number | No 2 kJ rule. Quittmann 2026 SEE 5.4 kJ / LoA −14.1 to +8.0 kJ is cross-method 3-min WEP vs modelled W′, not retest error | Protocol-specific repeatability before calling a change | Not a tank. Not 3-min WEP |
| Heart rate at fixed power | A 10-min steady segment | Cardiovascular trend | Confounded by heat, fuel, fatigue | Same segment every 1–2 weeks; judge over a month | No 5% pass/fail |
| Decoupling | Derived | Flag for a controlled repeat | High outdoors | Only after a repeated, similar ride | Friel bands are coaching practice |
| Resting heart rate | One quiet minute | Illness screen, weekly trend | Typical error ~10% vs worthwhile change ~2% (Buchheit, 2014) | 7-day mean | A high single morning is not a plan change |
| HRV (ln rMSSD) | A consistent morning protocol | Autonomic trend | Typical error ~12% vs worthwhile change ~3%; saturation in the very fit | 7-day mean | Optional. Composite with wellness if used |
| Wellness and sleep | Seconds | Acute response | Individual, but often more sensitive than objective markers (Saw, 2016) | Daily; act on the pattern | Not an overtraining diagnosis |
| Key-session execution | The session you were going to do anyway | Is the stimulus landing? | Motivation and pacing | Every hard session | The most specific interim test |

<a id="conflict-resolution-workflow"></a>
### Conflict-resolution workflow

Do this on a Sunday, or whenever the week is planned. It takes longer to read than to run.

1. **Anchor check.** Is FTP or critical power from a fresh test in the last 6–8 weeks, on the equipment you train with? If not, treat TSS, IF, and zones as provisional. Schedule the test before you interpret the chart.
2. **Diary check.** Hours and kilojoules versus the plan. Session-RPE versus the same sessions last block. Count completed hard sessions, not TSS.
3. **Response check.** Seven-day wellness, and seven-day resting heart rate or ln rMSSD if you collect them. One bad morning does not count. Three bad mornings plus rising session-RPE does.
4. **Outcome check.** If a test fell this week, compare it only with the previous test of the same protocol in the same state (fresh or preloaded). Ignore changes inside the published error (about 3% or ~10 W on a 20-minute test, unless you have your own error).
5. **Resolve conflicts in this order.** Outcome and key-session quality outrank internal load. Internal load outranks TSS/CTL. TSB outranks nothing.

| Pattern | What it usually means | What to do |
|---|---|---|
| Performance up, wellness stable, CTL up or flat | The block is working | Keep the structure. Do not add load just because the model “has room” |
| Performance up, wellness falling, session-RPE rising | Gain with a rising cost | Hold volume. Do not start the next progression until wellness stabilizes |
| CTL up, performance flat, session-RPE and wellness worse | Dose without adaptation | Reduce or redistribute. Do not add TSS to chase a higher CTL |
| CTL up, sessions feel easy, heart rate at fixed power down | FTP may be set low, so TSS is inflated, or the rider is genuinely fitter and under-stimulated | Confirm with a fresh test before you call it fitness or before you deload |
| TSS looks modest, session-RPE and heart rate are high | FTP set high, or heat, illness, low glycogen, poor sleep | Trust the internal signal for the next few days. Fix the anchor before rewriting zones |
| One HRV or resting-heart-rate outlier, wellness and sleep fine | Noise (Buchheit, 2014) | Do the planned session |
| HRV “green,” wellness and recent session quality poor | Marker disagreement; Alfonso (2025) found individual correlations are uneven | Skip the intensity. The composite vetoes the single marker |
| Decoupling over 5% on a hot or under-fueled ride | Drift, not a failed aerobic base | Repeat in control before changing easy-ride intensity |
| Fresh test up, preloaded effort unchanged | Ceiling changed, durability did not | Do not average them into one FTP. Decide which quality the next block is for |
| Multi-effort W′ moves, or one 5-minute effort jumps | Do not invent a threshold from the 3-min cross-method SEE | Quittmann 2026 does not establish 2 kJ as a W′ decision cut |

Health boundary, without turning this into a medical protocol: resting heart rate well above the personal seven-day mean with illness symptoms, chest pain, or unusual breathlessness is a stop-and-assess problem, not a TSB problem. The overtraining consensus (Meeusen and colleagues, 2013) treats that syndrome as a diagnosis of exclusion. A low HRV does not make it.

### 7–12 h versus a 20–30 h professional, again, for adaptation checks

The professional can test more often inside a large week and can watch durability across repeated long rides. The amateur should spend the scarce hard days on training, and spend one of them on a real test only at block boundaries. Life stress will move session-RPE and wellness more than it moves a professional’s, which makes those internal scores more, not less, useful. It also makes them easier to over-read: a bad work week is not a failed aerobic base. The performance test, done fresh after a normal week, is what separates the two.

---

<a id="open-questions"></a>
## Open questions

- No retrieved trial has randomized trained amateurs to a CTL or TSS target versus simple progression of recoverable, specific training. Until that exists, CTL-driven planning stays an untested layer on top of methods that do have dose–response associations.
- The fourth-power exponent and the 30-second window have not been shown to be optimal for predicting adaptation. Skiba’s 25-second alternative behaved similarly on his examples. That is an argument for not obsessing over the algorithm, not an argument that either algorithm measures stress.
- Fitted fitness–fatigue time constants are athlete- and metric-specific (Vermeire, 2021; Wallace, 2014). Nobody has established a cycling tau that should replace 42 and 7. Replacing them with another fixed pair would repeat the original mistake.
- The 95% rule is a poor individual estimator of hour power and an inconsistent estimator of maximal lactate steady state (Inglis, 2020; Lillo-Beviá, 2022; Sitko, 2022; Borszcz, 2018, 2019). In-sample corrections near 91% are not externally validated. What correction, if any, is stable across sexes and training states is open.
- Quittmann and Piehl (2026) settle the 3-minute all-out test as a biased CP estimator with reliable end-test power. They do not settle which multi-effort protocol a time-poor amateur should use, or how much familiarization is enough.
- HRV-guided training’s group effect on performance remains small after two 2021 meta-analyses. Alfonso (2025) is the right design direction — HRV plus resting heart rate plus wellness, in experienced cyclists — and the wrong control (no fixed plan). A 2026 perspective (Schaffarczyk and Sperlich) adds no new pooled effect.
- Rothschild and colleagues (2025) on decoupling and the first ventilatory threshold need independent confirmation before anyone replaces a performance test with a drift percentage. Their separate 2025 energy-expenditure models show load metrics tracking fuel use within a person after calibration. They do not belong in this note as a fueling system.
- Bossi and colleagues (2026) correctly attack duration-confounded correlations between TSS, Edwards TRIMP, and session-RPE. The retrieved record is a one-cyclist methodology paper. Replication across riders would be required before personal conversion equations were trustworthy.
- Women are scarce in the FTP, critical-power, and HRV-guided cycling trials cited here. Transfer of the error bars to female amateurs is plausible and unproven.
- Power-meter brand error was not re-measured for this note. Passfield and colleagues (2017) support field power as usable. A trend built across two uncompared meters is not.

---

<a id="references"></a>
## References

Vendor and software sources are labelled. They document formulas. They are not physiological trials. Abstracts were used where full text was not retrieved; those claims stay inside the abstract. Search windows included Europe PMC and, after access was restored, web search for 2025–2026 updates. Papers with a publication date after 2026-10-02 were not used.

- Alfonso C, Clarke DC, Capdevila L. Individual training prescribed by heart rate variability, heart rate and well-being scores in experienced cyclists. *Sci Rep*. 2025. doi:10.1038/s41598-025-13540-z. PMID 41028151. Abstract retrieved.
- Bartram JC, Thewlis D, Martin DT, Norton KI. Predicting critical power in elite cyclists: questioning the validity of the 3-minute all-out test. *Int J Sports Physiol Perform*. 2017. doi:10.1123/ijspp.2016-0376. PMID 27834562. Abstract.
- Borszcz FK, Tramontin AF, Bossi AH, Carminatti LJ, Costa VP. Functional threshold power in cyclists: validity of the concept and physiological responses. *Int J Sports Med*. 2018. doi:10.1055/s-0044-101546. PMID 29801189. Abstract.
- Borszcz FK, Tramontin AF, Costa VP. Reliability of the functional threshold power in competitive cyclists. *Int J Sports Med*. 2020. doi:10.1055/a-1018-1965. PMID 31952081. Abstract.
- Bossi AH, Matta G, Lima P, Bara-Filho M. Quantifying and comparing training load metrics in cycling: a methodology review. *Int J Sport Nutr Exerc Metab*. 2026;36(5):588-598. doi:10.1123/ijsnem.2026-0028. PMID 42315095. Abstract only; fit statistics not retrieved.
- Bourdon PC, Cardinale M, Murray A, et al. Monitoring athlete training loads: consensus statement. *Int J Sports Physiol Perform*. 2017. doi:10.1123/ijspp.2017-0208. PMID 28463642. Abstract.
- Buchheit M. Monitoring training status with HR measures: do all roads lead to Rome? *Front Physiol*. 2014. doi:10.3389/fphys.2014.00073. PMID 24578692. Full text consulted for the error table.
- Coggan AR. Normalized power, intensity factor and training stress score. TrainingPeaks. Published 10 February 2016, updated 11 May 2026. https://www.trainingpeaks.com/learn/articles/normalized-power-intensity-factor-training-stress/ Vendor explainer.
- Coyle EF, González-Alonso J. Cardiovascular drift during prolonged exercise: new perspectives. *Exerc Sport Sci Rev*. 2001. doi:10.1097/00003677-200104000-00009. PMID 11337829. Title and indexing; mechanism review not re-extracted in full.
- Denham J, Scott-Hamilton J, Hagstrom AD, Gray AJ. Cycling power outputs predict functional threshold power and maximum oxygen uptake. *J Strength Cond Res*. 2020;34(12):3489-3497. doi:10.1519/jsc.0000000000002253. PMID 28930880. Abstract. Cited to reject FTP-to-VO₂ conversion, not to supply an equation.
- Düking P, Zinner C, Trabelsi K, Reed JL, Holmberg HC. Monitoring and adapting endurance training on the basis of heart rate variability monitored by wearable technologies: a systematic review with meta-analysis. *J Sci Med Sport*. 2021. doi:10.1016/j.jsams.2021.04.012. PMID 34489178. Abstract.
- Foster C, Florhaug JA, Franklin J, et al. A new approach to monitoring exercise training. *J Strength Cond Res*. 2001. doi:10.1519/1533-4287(2001)015<0109:anatme>2.0.co;2. PMID 11708692. Method cited via secondary descriptions; trial numbers not retrieved.
- Foster C, Rodríguez-Marroyo JA, de Koning JJ. Monitoring training loads: the past, the present, and the future. *Int J Sports Physiol Perform*. 2017. doi:10.1123/ijspp.2016-0388. PMID 28253038. Abstract.
- Friel J. Estimating training stress score (TSS). TrainingPeaks. Published 21 September 2009, updated 13 April 2026. https://www.trainingpeaks.com/learn/articles/estimating-training-stress-score-tss/ Vendor formula.
- Friel J. Aerobic decoupling and heart rate drift explained. TrainingPeaks. Published 10 October 2008, updated 3 June 2026. https://www.trainingpeaks.com/coach-blog/aerobic-endurance-and-decoupling/ Coaching/vendor. Contains the 5% bands and states that no research-based duration rule exists.
- GoldenCheetah project. Glossary of terms, including NP, TSS, CTL/ATL/TSB, session-RPE, and decoupling. https://github.com/GoldenCheetah/GoldenCheetah/wiki/UG_Glossary Software documentation, retrieved 2026-10-02.
- Habets MA, de Jong J, de Groot S, Hesselink MKC, Sanders D. Comparison of modelled maximal lactate steady state with critical power in elite cyclists. 2026. doi:10.1055/a-2917-0233. PMID 42586158. Abstract.
- Halson SL. Monitoring training load to understand fatigue in athletes. *Sports Med*. 2014. doi:10.1007/s40279-014-0253-z. PMID 25200666. Full text consulted.
- Impellizzeri FM, Marcora SM, Coutts AJ. Internal and external training load: 15 years on. *Int J Sports Physiol Perform*. 2019. doi:10.1123/ijspp.2018-0935. PMID 30614348. Abstract.
- Impellizzeri FM, Tenan MS, Kempton T, Novak A, Coutts AJ. Acute:chronic workload ratio: conceptual issues and fundamental pitfalls. *Int J Sports Physiol Perform*. 2020. doi:10.1123/ijspp.2019-0864. PMID 32502973. Abstract.
- Inglis EC, Iannetta D, Passfield L, Murias JM. Maximal lactate steady state versus the 20-minute functional threshold power test in well-trained individuals. *Int J Sports Physiol Perform*. 2020. doi:10.1123/ijspp.2019-0214. PMID 31689684. Abstract.
- Javaloyes A, Sarabia JM, Lamberts RP, Moya-Ramón M. Training prescription guided by heart-rate variability in cycling. *Int J Sports Physiol Perform*. 2019. doi:10.1123/ijspp.2018-0122. PMID 29809080. Abstract.
- Karsten B, Jobson SA, Hopker J, Stevens L, Beedie C. Validity and reliability of critical power field testing. *Eur J Appl Physiol*. 2015. doi:10.1007/s00421-014-3001-z. PMID 25260244. Abstract.
- Karsten B, Petrigna L, Klose A, Bianco A, Townsend N, Triska C. Relationship between the critical power test and a 20-min functional threshold power test in cycling. *Front Physiol*. 2021. doi:10.3389/fphys.2020.613151. PMID 33551839. Full text consulted.
- Kellmann M, Bertollo M, Bosquet L, et al. Recovery and performance in sport: consensus statement. *Int J Sports Physiol Perform*. 2018. doi:10.1123/ijspp.2017-0759. PMID 29345524. Identified; recommendations not re-extracted.
- Klitzke Borszcz F, Ferreira Tramontin A, Pereira Costa V. Is the functional threshold power interchangeable with the maximal lactate steady state in trained cyclists? *Int J Sports Physiol Perform*. 2019. doi:10.1123/ijspp.2018-0572. PMID 30676826. Abstract.
- Lillo-Beviá JR, Courel-Ibáñez J, Cerezuela-Espejo V, Morán-Navarro R, Martínez-Cava A, Pallarés JG. Is the functional threshold power a valid metric to estimate the maximal lactate steady state in cyclists? *J Strength Cond Res*. 2022. doi:10.1519/jsc.0000000000003403. PMID 31714462. Abstract.
- Lucía A, Hoyos J, Santalla A, Earnest C, Chicharro JL. Tour de France versus Vuelta a España: which is harder? *Med Sci Sports Exerc*. 2003. doi:10.1249/01.mss.0000064999.82036.b4. PMID 12750600. Abstract. Zone weights not stated in the retrieved text.
- MacInnis MJ, Thomas ACQ, Phillips SM. The reliability of 4-minute and 20-minute time trials and their relationships to functional threshold power in trained cyclists. *Int J Sports Physiol Perform*. 2019. doi:10.1123/ijspp.2018-0100. PMID 29809063. Abstract.
- Mackey J, Horner K. What is known about the FTP20 test related to cycling? A scoping review. *J Sports Sci*. 2021. doi:10.1080/02640414.2021.1955515. PMID 34304689. Abstract.
- Manresa-Rocamora A, Sarabia JM, Javaloyes A, Flatt AA, Moya-Ramón M. Heart rate variability-guided training for enhancing cardiac-vagal modulation, aerobic fitness, and endurance performance: a methodological systematic review with meta-analysis. *Int J Environ Res Public Health*. 2021. doi:10.3390/ijerph181910299. PMID 34639599. Full text consulted for pooled effects.
- Manzi V, Iellamo F, Impellizzeri F, D'Ottavio S, Castagna C. Relation between individualized training impulses and performance in distance runners. *Med Sci Sports Exerc*. 2009. doi:10.1249/mss.0b013e3181a6a959. PMID 19812506. Abstract. Runners, not cyclists.
- Meeusen R, Duclos M, Foster C, et al. Prevention, diagnosis, and treatment of the overtraining syndrome: joint consensus statement of the ECSS and the ACSM. *Med Sci Sports Exerc*. 2013. doi:10.1249/mss.0b013e318279a10a. PMID 23247672. Identified; diagnostic algorithm not re-extracted.
- Montain SJ, Coyle EF. Influence of graded dehydration on hyperthermia and cardiovascular drift during exercise. *J Appl Physiol*. 1992. doi:10.1152/jappl.1992.73.4.1340. PMID 1447078. Title result; magnitudes not re-extracted.
- Mujika I. Quantification of training and competition loads in endurance sports: methods and applications. *Int J Sports Physiol Perform*. 2017. doi:10.1123/ijspp.2016-0403. PMID 27918666. Abstract.
- Passfield L, Hopker JG, Jobson S, Friel D, Zabala M. Knowledge is power: issues of measuring training and performance in cycling. *J Sports Sci*. 2017. doi:10.1080/02640414.2016.1215504. PMID 27686573. Abstract.
- Plews DJ, Laursen PB, Stanley J, Kilding AE, Buchheit M. Training adaptation and heart rate variability in elite endurance athletes: opening the door to effective monitoring. *Sports Med*. 2013. doi:10.1007/s40279-013-0071-8. PMID 23852425. Abstract.
- Quittmann OJ, Piehl MA. The 3-min all-out test in cycling: a systematic review and meta-analysis on its reliability and validity. *Eur J Appl Physiol*. 2026. doi:10.1007/s00421-026-06356-w. PMID 42479066. Full text.
- Rodríguez-Marroyo JA, Villa JG, García-López J, Foster C. Comparison of heart rate and session rating of perceived exertion methods of defining exercise load in cyclists. *J Strength Cond Res*. 2012. doi:10.1519/jsc.0b013e31823a4233. PMID 21997452. Abstract.
- Rothschild JA, Gallo G, Hamilton K, et al. Durability of the moderate-to-heavy intensity transition can be predicted using readily available markers of physiological decoupling. *Eur J Appl Physiol*. 2025. doi:10.1007/s00421-025-05815-0. PMID 40402269. Abstract.
- Rothschild JA, Hofmeyr S, McLaren SJ, Maunder E. A novel method to predict carbohydrate and energy expenditure during endurance exercise using measures of training load. *Sports Med*. 2025. doi:10.1007/s40279-024-02131-z. PMID 39487383. Abstract. Cited only to bound what load metrics track, not as fueling guidance.
- Sanders D, Abt G, Hesselink MKC, Myers T, Akubat I. Methods of monitoring training load and their relationships to changes in fitness and performance in competitive road cyclists. *Int J Sports Physiol Perform*. 2017. doi:10.1123/ijspp.2016-0454. PMID 28095061. Abstract.
- Saw AE, Main LC, Gastin PB. Monitoring the athlete training response: subjective self-reported measures trump commonly used objective measures: a systematic review. *Br J Sports Med*. 2016. doi:10.1136/bjsports-2015-094758. PMID 26423706. Full text consulted.
- Schaffarczyk M, Sperlich B. Heart rate variability-guided endurance training: evaluating strengths, weaknesses, opportunities, and threats. *Front Sports Act Living*. 2026. doi:10.3389/fspor.2026.1858271. PMID 42724227. Abstract.
- Schwellnus M, Soligard T, Alonso JM, et al. How much is too much? (Part 2) International Olympic Committee consensus statement on load in sport and risk of illness. *Br J Sports Med*. 2016. doi:10.1136/bjsports-2016-096572. PMID 27535991. Abstract.
- Sitko S, Cirer-Sastre R, Corbi F, López-Laval I. Functional threshold power as an alternative to lactate thresholds in road cycling. *J Strength Cond Res*. 2022. doi:10.1519/jsc.0000000000004070. PMID 34127613. Abstract.
- Sitko S, Cirer-Sastre R, López-Laval I. Time to exhaustion at estimated functional threshold power in road cyclists of different performance levels. *J Sci Med Sport*. 2022. doi:10.1016/j.jsams.2022.06.007. PMID 35835698. Abstract; sample size not in the retrieved text.
- Skiba PF. Analysis of power output and training stress in cyclists: the development of the BikeScore algorithm. PhysFarm Training Systems; 2008. https://raw.githubusercontent.com/GoldenCheetah/GoldenCheetah/master/doc/user/bikescore.pdf Vendor/methods note, not a peer-reviewed trial.
- Soligard T, Schwellnus M, Alonso JM, et al. How much is too much? (Part 1) International Olympic Committee consensus statement on load in sport and risk of injury. *Br J Sports Med*. 2016. doi:10.1136/bjsports-2016-096581. PMID 27535989. Abstract.
- TrainingPeaks. What is the performance management chart? Published 16 June 2015, updated 16 May 2026. https://www.trainingpeaks.com/learn/articles/what-is-the-performance-management-chart/ Vendor. States 7-day and 42-day exponential averages and yesterday-minus-yesterday form.
- Valenzuela PL, Morales JS, Foster C, Lucía A, de la Villa P. Is the functional threshold power a valid surrogate of the lactate threshold? *Int J Sports Physiol Perform*. 2018. doi:10.1123/ijspp.2018-0008. PMID 29745765. Abstract.
- van Erp T, Foster C, de Koning JJ. Relationship between various training-load measures in elite cyclists during training, road races, and time trials. *Int J Sports Physiol Perform*. 2019. doi:10.1123/ijspp.2017-0722. PMID 30300025. Abstract.
- van Erp T, Hoozemans MPM, Foster C, de Koning JJ. The influence of exercise intensity on the association between kilojoules spent and various training loads in professional cycling. *Int J Sports Physiol Perform*. 2019. doi:10.1123/ijspp.2018-0877. PMID 30958053. Abstract.
- van Erp T, Sanders D, de Koning JJ. Training characteristics of male and female professional road cyclists: a 4-year retrospective analysis. *Int J Sports Physiol Perform*. 2020. doi:10.1123/ijspp.2019-0320. PMID 31722298. Abstract. Weekly hours not reported in the retrieved text.
- Vermeire K, Van de Casteele F, Gosseries M, Bourgois JG, Ghijs M. The influence of different training load quantification methods on the fitness-fatigue model. *Int J Sports Physiol Perform*. 2021. doi:10.1123/ijspp.2020-0662. PMID 33691278. Abstract.
- Vesterinen V, Nummela A, Heikura I, et al. Individual endurance training prescription with heart rate variability. *Med Sci Sports Exerc*. 2016. doi:10.1249/mss.0000000000000910. PMID 26909534. Abstract. Recreational runners.
- Wallace LK, Slattery KM, Coutts AJ. A comparison of methods for quantifying training load: relationships between modelled and actual training responses. *Eur J Appl Physiol*. 2014. doi:10.1007/s00421-013-2745-1. PMID 24104194. Abstract. Runners.
- Wingo JE, Lafrenz AJ, Ganio MS, Edwards GL. Cardiovascular drift is related to reduced maximal oxygen uptake during heat stress. *Med Sci Sports Exerc*. 2005. doi:10.1249/01.mss.0000152731.33450.95. PMID 15692320. Title result; magnitudes not re-extracted.
- Windt J, Gabbett TJ. Is it all for naught? What does mathematical coupling mean for acute:chronic workload ratios? *Br J Sports Med*. 2019. doi:10.1136/bjsports-2017-098925. PMID 29807930. Identified; not expanded.
