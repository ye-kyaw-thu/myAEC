# myAEC: ASR (Generative) Error Correction Corpus

This repository contains the **Burmese Automatic Speech Recognition (ASR) Error Correction (AEC) Dataset**, created as part of the paper:

**ASR Error Correction in Low-Resource Burmese with Alignment-Enhanced Transformers using Phonetic Features**
*(Ye Bhone Lin, Thura Aung, Thazin Myint Oo, Ye Kyaw Thu)*

This dataset provides **parallel data of:**

* ASR output (with errors)
* Ground-truth transcripts
* Alignment files 
* IPA annotation features 

It is the first dataset focused specifically on **post-ASR error correction for Burmese** and is designed to support research in low-resource speech technologies, NMT-style correction models, and phonetic/linguistic feature integration.

## Source Speech Corpora

We used two open-source Burmese speech datasets:

| Dataset   | Train Hours | Test Hours | MOSNet |
| --------- | ----------- | ---------- | ------ |
| OpenSLR80 | 3.70        | 0.42       | 4.06   |
| FLEURS    | 15.95       | 1.64       | 4.14   |

These speech datasets are **NOT** redistributed here—only the **post-ASR text pairs** are included.

## License Information
Creative Commons Attribution-NonCommercial-Share Alike 4.0 International (CC BY-NC-SA 4.0) License.  
[[Detail Information]](https://creativecommons.org/licenses/by-nc-sa/4.0/)  

## How the Dataset Was Created

1. Fine-tuned Burmese ASR models:

   * Whisper Tiny / Small / Medium / Large
   * MMS-1B ASR

2. Generated ASR transcripts for:

   * Original audio
   * Data-augmented audio (speed, pitch, VTLP, noise, etc.)

3. Cleaned and syllable-segmented text using **myWord**.

4. Created **parallel pairs**:

   * `ASR Error → Ground Truth`

5. Extracted optional features:

   * **IPA phonetic features** (via CRF G2P)
   * **Alignment features** (fast-align)


## Dataset Statistics

| Split     | Sentences | Err Syllables | GT Syllables |
| --------- | --------- | ------------- | ------------ |
| Original  | 31.7k     | 1.25M         | 1.22M        |
| Augmented | 55.9k     | 2.17M         | 2.19M        |
| Test      | 3.19k     | 0.13M         | 0.12M        |

## Data Samples

Our original parallel corpus train and test split

```
>>> head -3 data/v1/original-data-v1/*
==> data/v1/original-data-v1/aec_without_feat.err.test.txt <==
အ သ စ လော့ တော ခြောင်း အ ဝါ သည် တွက် များ ကိုး စား ရန် သား ခောင် အ တွက် မြေ ပြင် ပေါ် တွင်၎င်း တို့ သွား ရောက် ခဲ့ သ ည့် နေ ရာ အား အ နံ့ ခံ ခြင်း ပြင် အ နံ မှာ သူ ဆ င့် နောက် ရောင် ခ ယ ၍ လှာ ဖွေး ကြောင်း သိပ္ပံ ပ ညာ ရှစ် များ က ထင် မြင် ကြ သည်
အ လောင်း သည် ရေ်း နေ ရာ တွင် ပေါ် လာ သည် မှာ သ ရပ် ပင် ရှိ ပြီး ဟု ရဲ ဌာ န က ဆို ပါ သည်
ဘူ ရှ် ၏ ပြော ၍ေး ဆို ခွ င့်း ရှိ သူ ဂျော ဒန် ဂျော် ဒ ရို က မြောက် ကို ရီး ယား နိုင် ငံ ၏ က တိ က ဝတ် သည် ကို ကို ရီး ယား ကျွန်း စွယ် အား အ တည် ပြု နိုင် သည် နျူ က လီး ယား စစ် ဆဉ် ရေး ဒေ သား ဖြစ် စေ ရေး စွမ်း ဆောင် မှု ရီ မန် ဂျက် ကို လျှောက် လဲ်း ရာ တွင် အ ဓိ က ကျ သော လေ က ထစ် တစ် ခု ဖြစ် သည် ဟု တုံး သုံး ပြော ဆို ခဲ့ သည်

==> data/v1/original-data-v1/aec_without_feat.err.train.txt <==
2 0 1 5 ခု နှစ် နောင်း ပိုင်း တွင် တို ကီ နက် သည် အ စ တိုး နတ် ရေ ဒီ ယို ကို လက် အောက် ခံ ရေ ဒီ ယို အ သံ လွှ င့် စ ခန်း တစ် ခု အ ဖြစ် တည် ဆောက် ခဲ့ သည်
သွေး စီး ဆင်း မှု ကို ရပ် တ န့် ရန် သွေး ထိန်း စည်း များ နှ င့် သွေး လွှတ် ကျော အ ဆို့ များ အ ပြ င့် လူ နာ များ သွေး ပုတ် ပွ ခြင်း မ ဖြစ် စေ ရန် ဖြတ် တောက် မှု တွင် ပို ကျွမ်း ကျင် လာ သည်
ခေတ် ဆန် သော မြို့ တော် ကာ ဆာ ပ လန် ကာ ကို ခ ရစ် တောင် မ ပေါ် မီ 1 0် ရာ စု တွင် ဘာ ဘာ ငါး ဖမ်း သ မား များ ခ တည် ထောင် ခဲ့ ခြင်း ဖြစ် ကာ ဖ နီး ရှမ်း များ ရို မန် များ နှ င့် အန် ဖာ ဟု ခေါ် သော နည်း ဖီး ဝါ ဆိုင် ရာ စိပ် ကမ်း အ ဖြင် မ ရီ နစ် တို့ က သုံး ပြု ခဲ့ ပါ သည်

==> data/v1/original-data-v1/aec_without_feat.gt.test.txt <==
အော့ ဆ လော့ တော ကြောင် အ ဝါ သည် ကြွက် များ ကို စား ရန် သား ကောင် အ တွက် မြေ ပြင် ပေါ် တွင်  ၎င်း တို့ သွား ရောက် ခဲ့ သ ည့် နေ ရာ အား အ နံ့ ခံ ခြင်း ဖြ င့် အ နံ့ မှ တ ဆ င့် နောက် ယောင် ခံ ၍ ရှာ ဖွေ ကြောင်း သိပ္ပံ ပ ညာ ရှင် များ က ထင် မြင် ကြ သည်
အ လောင်း သည် ယင်း နေ ရာ တွင် ပေါ် လာ သည် မှာ တစ် ရက် ပင် ရှိ ပြီ ဟု ရဲ ဌာ န က ဆို ပါ သည်
ဘု ရှ် ၏ ပြော ရေး ဆို ခွ င့် ရှိ သူ ဂျော ဒန် ဂျွန် ဒ ရိုး က မြောက် ကို ရီး ယား နိုင် ငံ ၏ က တိ က ဝတ် သည် ကို ရီး ယား ကျွန်း ဆွယ် အား အ တည် ပြု နိုင် သ ည့် နျူ လက် နက် ကင်း စင် ရေး ဒေ သ ဖြစ် စေ ရေး စွမ်း ဆောင် မှု ရည် မှန်း ချက် ကို လျှောက် လှမ်း ရာ တွင် အ ဓိ က ကျ သော လှေ ကား ထစ် တစ် ခု ဖြစ် သည် ဟု သုံး နှုန်း ပြော ဆို ခဲ့ သည်

==> data/v1/original-data-v1/aec_without_feat.gt.train.txt <==
၂ ၀ ၁ ၅ ခု နှစ် နှောင်း ပိုင်း တွင် တို ဂီ နက် သည် အ စ တို နက် ရေ ဒီ ယို ကို လက် အောက် ခံ ရေ ဒီ ရို အ သံ လွ င့် စ ခန်း တစ် ခု အ ဖြစ် တည် ထောင် ခဲ့ သည်
သွေး စီး ဆင်း မှု ကို ရပ် တ န့် ရန် သွေး ထိန်း စည်း များ နှ င့် သွေး လွှတ် ကြော အ ဆို့ များ အ ပြင် လူ နာ များ သွေး ပုပ် ပွ ခြင်း မ ဖြစ် စေ ရန် ဖြတ် တောက် မှု တွင် ပို ကျွမ်း ကျင် လာ သည်
ခေတ် ဆန် သော မြို့ တော် ကာ ဆာ ဘ လန် ကာ ကို ခ ရစ် တော် မ ပေါ် မီ ၁ ၀ ရာ စု တွင် ဘာ ဘာ ငါး ဖမ်း သ မား များ က တည် ထောင် ခဲ့ ခြင်း ဖြစ် ကာ ဖ နီး ရှန်း များ  ရို မန် များ  နှ င့် အန် ဖာ ဟု ခေါ် သော နည်း ဗျူ ဟာ ဆိုင် ရာ ဆိပ် ကမ်း အ ဖြစ် မ ရီ နစ် တို့ က အ သုံး ပြု ခဲ့ ပါ သည်
```

Data with IPA automatic annotation and augmented data are in tsv_files/

```
>>> head -3 data/v1/tsv_files/original_corpus/*
==> data/v1/tsv_files/original_corpus/AEC_IPA.tsv <==
ASR_Error	Correct
နှစ်￨n̥ə ထော￨tʰɔ́ င့်￨pə စင်း￨sɪ́ɴ ကား￨gə ခု￨gṵ နှစ်￨n̥ɪʔ နောင်း￨ʔɔ̀ ပိုင်း￨páɪɴ တွင်￨dwɪ̀ɴ တို￨tò ကီ￨kì နက်￨nɛʔ သည်￨ðɛ̀ အ￨ʔə ဆက်￨sʰɛʔ တိုး￨sə နက်￨nɛʔ တွေ￨dwè တီ￨tì ယို￨jò ကို￨kò လက်￨lɛʔ အောက်￨ʔaʊʔ ခံ￨gàɴ တေး￨té တီး￨tí ယို￨jò အ￨ʔə သံ￨θàɴ လွ￨zú င့်￨gàɴ စ￨sə ခန်း￨kʰáɴ တစ်￨tə ခု￨kʰṵ အ￨ʔə ဖြင်း￨pə တည်￨tì ဆောက်￨sʰaʊʔ ခဲ့￨dʑaʊʔ သည်￨ðɛ̀	၂ ၀ ၁ ၅ ခု နှစ် နှောင်း ပိုင်း တွင် တို ဂီ နက် သည် အ စ တို နက် ရေ ဒီ ယို ကို လက် အောက် ခံ ရေ ဒီ ရို အ သံ လွ င့် စ ခန်း တစ် ခု အ ဖြစ် တည် ထောင် ခဲ့ သည် 
သူ￨θù အေး￨ʔé စီး￨sí စဉ်း￨sɪ́ɴ မှု￨m̥ṵ ကို￨kò ရက်￨ɹɛʔ တ￨tə န့်￨ɹḭ ရန်￨jàɴ သူ￨ðù အေး￨ʔé ထိန်း￨déɪɴ စီး￨sí များ￨mjá နဲ့￨nɛ̰ သွေး￨ðwé လွှတ်￨ɬʊʔ ကျော်￨dʑɔ̀ အ￨ʔə စို့￨so̰ များ￨mjá အ￨ʔə ပြင်￨pjɪ̀ɴ လူ￨lù နာ￨nà များ￨mjá သွေး￨θwé ပုတ်￨mə ပွ￨pwa̰ ခြင်း￨ʥɪ́ɴ မ￨mə ဖြစ်￨pʰjɪʔ ဆေ￨sʰè ရန်￨jàɴ ဖြတ်￨pʰjaʔ တောက်￨taʊʔ မှု￨m̥ṵ တွင်￨twɪ̀ɴ ပို￨pò ကျွမ်း￨tɕwáɴ ကျင်￨tɕɪ̀ɴ လာ￨là သည်￨ðὲ	သွေး စီး ဆင်း မှု ကို ရပ် တ န့် ရန် သွေး ထိန်း စည်း များ နှ င့် သွေး လွှတ် ကြော အ ဆို့ များ အ ပြင် လူ နာ များ သွေး ပုပ် ပွ ခြင်း မ ဖြစ် စေ ရန် ဖြတ် တောက် မှု တွင် ပို ကျွမ်း ကျင် လာ သည် 

==> data/v1/tsv_files/original_corpus/AEC_Without_Feat.tsv <==
ASR_Error	Correct
2 0 1 5 ခု နှစ် နောင်း ပိုင်း တွင် တို ကီ နက် သည် အ စ တိုး နတ် ရေ ဒီ ယို ကို လက် အောက် ခံ ရေ ဒီ ယို အ သံ လွှ င့် စ ခန်း တစ် ခု အ ဖြစ် တည် ဆောက် ခဲ့ သည်	၂ ၀ ၁ ၅ ခု နှစ် နှောင်း ပိုင်း တွင် တို ဂီ နက် သည် အ စ တို နက် ရေ ဒီ ယို ကို လက် အောက် ခံ ရေ ဒီ ရို အ သံ လွ င့် စ ခန်း တစ် ခု အ ဖြစ် တည် ထောင် ခဲ့ သည် 
သွေး စီး ဆင်း မှု ကို ရပ် တ န့် ရန် သွေး ထိန်း စည်း များ နှ င့် သွေး လွှတ် ကျော အ ဆို့ များ အ ပြ င့် လူ နာ များ သွေး ပုတ် ပွ ခြင်း မ ဖြစ် စေ ရန် ဖြတ် တောက် မှု တွင် ပို ကျွမ်း ကျင် လာ သည်	သွေး စီး ဆင်း မှု ကို ရပ် တ န့် ရန် သွေး ထိန်း စည်း များ နှ င့် သွေး လွှတ် ကြော အ ဆို့ များ အ ပြင် လူ နာ များ သွေး ပုပ် ပွ ခြင်း မ ဖြစ် စေ ရန် ဖြတ် တောက် မှု တွင် ပို ကျွမ်း ကျင် လာ သည် 

==> data/v1/tsv_files/original_corpus/Test_IPA_AEC.tsv <==
ASR_Error	Correct
အ￨ʔə သ￨ðə စ￨zə လော့￨θθə တော￨tɔ́ ခြောင်း￨tɕʰáʊɴ အ￨ʔə ဝါ￨wà သည်￨ðì တွက်￨twɛʔ များ￨mjá ကိုး￨kó စား￨sá ရန်￨jàɴ သား￨ðá ခောင်￨bɛ̰ အ￨ʔə တွက်￨twɛʔ မြေ￨mjè ပြင်￨bjɪ̀ɴ ပေါ်￨pɔ̀ တွင်၎င်း￨gə တို့￨to̰ သွား￨θwá ရောက်￨jaʊʔ ခဲ့￨jaʊʔ သ￨ðə ည့်￨hʊ́ɴ နေ￨nè ရာ￨jà အား￨ʔá အ￨ʔə နံ့￨nə ခံ￨gàɴ ခြင်း￨dʑɪ́ɴ ပြင်￨bjɪ̀ɴ အ￨ʔə နံ￨nàɴ မှာ￨m̥à သူ￨ðə ဆ￨sʰə င့်￨gɛ́ နောက်￨naʊʔ ရောင်￨jàʊɴ ခ￨kʰə ယ￨ja̰ ၍￨x လှာ￨zoʊʔ ဖွေး￨pʰwé ကြောင်း￨dʑáʊɴ သိပ္ပံ￨gàɴ ပ￨pjɪ̀ɴ ညာ￨ɲà ရှစ်￨ʃɪʔ များ￨mjá က￨gə ထင်￨tʰɪ̀ɴ မြင်￨mjɪ̀ɴ ကြ￨gòʊɴ သည်￨θɛ̀	အော့ ဆ လော့ တော ကြောင် အ ဝါ သည် ကြွက် များ ကို စား ရန် သား ကောင် အ တွက် မြေ ပြင် ပေါ် တွင်  ၎င်း တို့ သွား ရောက် ခဲ့ သ ည့် နေ ရာ အား အ နံ့ ခံ ခြင်း ဖြ င့် အ နံ့ မှ တ ဆ င့် နောက် ယောင် ခံ ၍ ရှာ ဖွေ ကြောင်း သိပ္ပံ ပ ညာ ရှင် များ က ထင် မြင် ကြ သည်
အ￨ʔə လောင်း￨láʊɴ သည်￨ðɛ̀ ရေ်း￨bjè နေ￨nè ရာ￨jà တွင်￨dwɪ̀ɴ ပေါ်￨pɔ̀ လာ￨là သည်￨ðì မှာ￨m̥à သ￨θə ရပ်￨jaʔ ပင်￨pɪ̀ɴ ရှိ￨ʃḭ ပြီး￨bjí ဟု￨hṵ ရဲ￨jɛ́ ဌာ￨tʰà န￨na̰ က￨kə ဆို￨sʰò ပါ￨bà သည်￨ðɛ̀	အ လောင်း သည် ယင်း နေ ရာ တွင် ပေါ် လာ သည် မှာ တစ် ရက် ပင် ရှိ ပြီ ဟု ရဲ ဌာ န က ဆို ပါ သည်

==> data/v1/tsv_files/original_corpus/Test_Without_Feat_AEC.tsv <==
ASR_Error	Correct
အ သ စ လော့ တော ခြောင်း အ ဝါ သည် တွက် များ ကိုး စား ရန် သား ခောင် အ တွက် မြေ ပြင် ပေါ် တွင်၎င်း တို့ သွား ရောက် ခဲ့ သ ည့် နေ ရာ အား အ နံ့ ခံ ခြင်း ပြင် အ နံ မှာ သူ ဆ င့် နောက် ရောင် ခ ယ ၍ လှာ ဖွေး ကြောင်း သိပ္ပံ ပ ညာ ရှစ် များ က ထင် မြင် ကြ သည်	အော့ ဆ လော့ တော ကြောင် အ ဝါ သည် ကြွက် များ ကို စား ရန် သား ကောင် အ တွက် မြေ ပြင် ပေါ် တွင်  ၎င်း တို့ သွား ရောက် ခဲ့ သ ည့် နေ ရာ အား အ နံ့ ခံ ခြင်း ဖြ င့် အ နံ့ မှ တ ဆ င့် နောက် ယောင် ခံ ၍ ရှာ ဖွေ ကြောင်း သိပ္ပံ ပ ညာ ရှင် များ က ထင် မြင် ကြ သည်
အ လောင်း သည် ရေ်း နေ ရာ တွင် ပေါ် လာ သည် မှာ သ ရပ် ပင် ရှိ ပြီး ဟု ရဲ ဌာ န က ဆို ပါ သည်	အ လောင်း သည် ယင်း နေ ရာ တွင် ပေါ် လာ သည် မှာ တစ် ရက် ပင် ရှိ ပြီ ဟု ရဲ ဌာ န က ဆို ပါ သည်
```

```
>>> head -3 data/v1/tsv_files/augmentation_corpus/*
==> data/v1/tsv_files/augmentation_corpus/Aug_IPA.tsv <==
ASR_Error	Correct
2￨x 0￨x 1￨x 5￨x ခု￨gṵ နှစ်￨n̥ɪʔ နောင်း￨bì ပိုင်း￨páɪɴ တွင်￨dwɪ̀ɴ တို￨tò ကီ￨kì နက်￨nɛʔ သည်￨θì အ￨ʔə စ￨sə တိုး￨dó နတ်￨naʔ ရေ￨ɹè ဒီ￨dì ယို￨jò ကို￨kò လက်￨lɛʔ အောက်￨ʔaʊʔ ခံ￨kʰàɴ ရေ￨ɹè ဒီ￨dì ယို￨jò အ￨ʔə သံ￨θàɴ လွှ￨ɬwa̰ င့်￨dʑʊ̀ɴ စ￨sə ခန်း￨kʰáɴ တစ်￨tə ခု￨kʰṵ အ￨ʔə ဖြစ်￨pʰjɪʔ တည်￨tì ဆောက်￨zaʊʔ ခဲ့￨dʑaʊʔ သည်￨ðɛ̀	၂ ၀ ၁ ၅ ခု နှစ် နှောင်း ပိုင်း တွင် တို ဂီ နက် သည် အ စ တို နက် ရေ ဒီ ယို ကို လက် အောက် ခံ ရေ ဒီ ရို အ သံ လွ င့် စ ခန်း တစ် ခု အ ဖြစ် တည် ထောင် ခဲ့ သည် 
သွေး￨θwé စီး￨sí ဆင်း￨zɪ́ɴ မှု￨m̥ṵ ကို￨kò ရပ်￨jaʔ တ￨tə န့်￨ɹḭ ရန်￨jàɴ သွေး￨ðwé ထိန်း￨déɪɴ စည်း￨sí များ￨mjá နှ￨n̥ə င့်￨to̰ သွေး￨θwé လွှတ်￨ɬʊʔ ကျော￨tɕɔ́ အ￨ʔə ဆို့￨sʰo̰ များ￨mjá အ￨ʔə ပြ￨pja̰ င့်￨dòʊɴ လူ￨lù နာ￨nà များ￨mjá သွေး￨θwé ပုတ်￨boʊʔ ပွ￨pwa̰ ခြင်း￨ʥɪ́ɴ မ￨mə ဖြစ်￨pʰjɪʔ စေ￨sè ရန်￨jàɴ ဖြတ်￨pʰjaʔ တောက်￨taʊʔ မှု￨m̥ṵ တွင်￨twɪ̀ɴ ပို￨pò ကျွမ်း￨tɕwáɴ ကျင်￨tɕɪ̀ɴ လာ￨là သည်￨ðì	သွေး စီး ဆင်း မှု ကို ရပ် တ န့် ရန် သွေး ထိန်း စည်း များ နှ င့် သွေး လွှတ် ကြော အ ဆို့ များ အ ပြင် လူ နာ များ သွေး ပုပ် ပွ ခြင်း မ ဖြစ် စေ ရန် ဖြတ် တောက် မှု တွင် ပို ကျွမ်း ကျင် လာ သည် 

==> data/v1/tsv_files/augmentation_corpus/Aug_Without_Feat.tsv <==
ASR_Error	Correct
2 0 1 5 ခု နှစ် နောင်း ပိုင်း တွင် တို ကီ နက် သည် အ စ တိုး နတ် ရေ ဒီ ယို ကို လက် အောက် ခံ ရေ ဒီ ယို အ သံ လွှ င့် စ ခန်း တစ် ခု အ ဖြစ် တည် ဆောက် ခဲ့ သည်	၂ ၀ ၁ ၅ ခု နှစ် နှောင်း ပိုင်း တွင် တို ဂီ နက် သည် အ စ တို နက် ရေ ဒီ ယို ကို လက် အောက် ခံ ရေ ဒီ ရို အ သံ လွ င့် စ ခန်း တစ် ခု အ ဖြစ် တည် ထောင် ခဲ့ သည် 
သွေး စီး ဆင်း မှု ကို ရပ် တ န့် ရန် သွေး ထိန်း စည်း များ နှ င့် သွေး လွှတ် ကျော အ ဆို့ များ အ ပြ င့် လူ နာ များ သွေး ပုတ် ပွ ခြင်း မ ဖြစ် စေ ရန် ဖြတ် တောက် မှု တွင် ပို ကျွမ်း ကျင် လာ သည်	သွေး စီး ဆင်း မှု ကို ရပ် တ န့် ရန် သွေး ထိန်း စည်း များ နှ င့် သွေး လွှတ် ကြော အ ဆို့ များ အ ပြင် လူ နာ များ သွေး ပုပ် ပွ ခြင်း မ ဖြစ် စေ ရန် ဖြတ် တောက် မှု တွင် ပို ကျွမ်း ကျင် လာ သည် 
```

We also release our alignment files trained using fastalign in alignment-files/
```
>>> head -3 data/v1/alignment-files/*
==> data/v1/alignment-files/augmented_with_feat.align <==
0-0
0-0 1-1 2-2 3-3 4-4 5-5 7-6 7-7 8-8 9-9 10-10 11-11 12-12 13-13 14-14 9-15 11-16 17-17 18-18 19-19 20-20 21-21 22-22 23-23 24-24 25-25 26-26 27-27 28-28 29-29 30-30 31-31 32-32 33-33 34-34 35-35 36-36 37-37 39-38 39-39 40-40
0-0 1-1 2-2 3-3 4-4 5-5 6-6 7-7 8-8 9-9 10-10 11-11 12-12 13-13 14-14 15-15 16-16 17-17 18-18 19-19 20-20 21-21 24-23 25-24 26-25 27-26 27-27 29-28 30-29 31-30 32-31 33-32 34-33 35-34 36-35 37-36 38-37 39-38 40-39 41-40 42-41 43-42

==> data/v1/alignment-files/augmented_without_feat_1.align <==
0-0
0-0 1-1 2-2 3-3 4-4 5-5 6-6 7-7 8-8 9-9 10-10 11-11 12-12 13-13 14-14 9-15 11-16 17-17 18-18 19-19 20-20 21-21 22-22 23-23 24-24 25-25 26-26 27-27 28-28 29-29 30-30 31-31 32-32 33-33 34-34 35-35 36-36 37-37 37-38 39-39 40-40
0-0 1-1 2-2 3-3 4-4 5-5 6-6 7-7 8-8 9-9 10-10 11-11 12-12 13-13 14-14 15-15 16-16 17-17 18-18 19-19 20-20 21-21 22-22 24-23 25-24 26-25 27-26 29-27 29-28 30-29 31-30 32-31 33-32 34-33 35-34 36-35 37-36 38-37 39-38 40-39 41-40 42-41 43-42

==> data/v1/alignment-files/original_with_feat.align <==
0-0
0-0 1-1 1-2 1-3 5-4 6-5 8-6 8-7 9-8 10-9 11-10 12-11 13-12 14-13 15-14 10-15 17-16 20-17 19-18 20-19 21-20 22-21 23-22 24-23 27-24 27-25 27-26 28-27 29-28 29-29 31-30 32-31 33-32 34-33 35-34 36-35 38-37 40-38 40-39 41-40
16-0 2-1 3-2 4-3 5-4 6-5 7-6 8-7 9-8 16-9 12-10 13-11 14-12 15-13 15-14 16-15 17-16 16-17 19-18 27-19 21-20 22-21 23-22 24-23 25-24 26-25 27-26 27-27 29-28 30-29 31-30 32-31 33-32 34-33 35-34 36-35 37-36 38-37 39-38 40-39 41-40 42-41 43-42

==> data/v1/alignment-files/original_without_feat.align <==
0-0
0-0 1-1 2-2 3-3 4-4 5-5 6-6 7-7 8-8 9-9 10-10 11-11 12-12 13-13 14-14 9-15 16-16 17-17 18-18 19-19 20-20 21-21 22-22 23-23 24-24 25-25 26-26 27-27 28-28 29-29 30-30 31-31 32-32 33-33 34-34 35-35 36-36 37-37 37-38 39-39 40-40
0-0 1-1 2-2 3-3 4-4 5-5 6-6 7-7 8-8 9-9 10-10 11-11 12-12 13-13 14-14 15-15 16-16 17-17 18-18 19-19 20-20 21-21 22-22 24-23 25-24 26-25 27-26 27-27 29-28 30-29 31-30 32-31 33-32 34-33 35-34 36-35 37-36 38-37 39-38 40-39 41-40 42-41 43-42
```


## Baseline Models & Code

We used:

* **OpenNMT-py** for AEC Transformer training
* **CRF-suite** for G2IPA (IPA extraction)
* **fast-align** for word alignment
* **transformers** (OpenAI Whisper finetuning)

Config files and scripts will be provided in:

```
/code-and-configs/notebook-examples # OpenNMT Training and Inference Example Notebooks
/code-and-configs/opennmt-config-files # Configuration files for our experiments
```

## Citation

If you use this **dataset** or **finetuned whisper models**, please cite:

```
@inproceedings{lin2025aec,
title={ASR Error Correction in Low-Resource Burmese with Alignment-Enhanced Transformers using Phonetic Features},
author={Lin, Ye Bhone and Aung, Thura and Thu, Ye Kyaw and Oo, Thazin Myint},
booktitle={2025 20th International Joint Symposium on Artificial Intelligence and Natural Language Processing (iSAI-NLP)},
pages={1--6},
year={2025},
keywords={Burmese language; Automatic Speech Recognition; ASR Error Correction; IPA; Alignment; Transformer},
location={Phuket, Thailand}
}
```

## Acknowledgments

This work was supported by **Language Understanding Lab (Myanmar)**.

Thanks to the contributors of OpenSLR80, FLEURS, myWord, myG2P, and fast-align.

## Contact

* Ye Kyaw Thu — [yekyaw.thu@nectec.or.th](mailto:yekyaw.thu@nectec.or.th)
* Ye Bhone Lin — [yebhonelin10@gmail.com](mailto:yebhonelin10@gmail.com)
* Thura Aung — [66011606@kmitl.ac.th](mailto:66011606@kmitl.ac.th)
