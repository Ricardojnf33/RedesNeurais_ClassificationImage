Projeto de Redes Neurais - Professor : Vitor Casadei
Aluno Ricardo José Nunes Fernandes
Dataset - Lion ; Tiger ; Cow
Pré-processameto de dados
Iremos utilizar um dataset composto por três classes ( Lion ; Tiger ; Cow ) retirados do google imagens, organizado e postado em meu github (Ricardojnf33) Os dados estão divididos em dois conjuntos: "train" e "val" e são compostos por 333 iamgens de cada classe, totalizando 999 imagens.

Abaixo está a maneira de preparar os dados:

[4]
0s
  1
!rm -rf RedesNeurais_ClassificationImage/ val/ PetImages/ PetImagesPetImages/ PetImagesval/
Realizando o clone do repositório ( Github )
[5]
16s
  1
!git clone https://github.com/Ricardojnf33/RedesNeurais_ClassificationImage.git
Cloning into 'RedesNeurais_ClassificationImage'...
remote: Enumerating objects: 330, done.
remote: Counting objects: 100% (330/330), done.
remote: Compressing objects: 100% (325/325), done.
remote: Total 330 (delta 2), reused 327 (delta 2), pack-reused 0
Receiving objects: 100% (330/330), 212.29 MiB | 31.58 MiB/s, done.
Resolving deltas: 100% (2/2), done.
Checking out files: 100% (999/999), done.
Reorganizando pastas para criação de diretórios
[6]
1s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
import os
import shutil
import re

base_dir = "PetImages"
try:
    os.makedirs("PetImages")
except OSError:
    print ("Creation of the directory %s failed")
else:
    print ("Successfully created the directory %s ")
dataset_dir = "RedesNeurais_ClassificationImage/train"

# Create training folder
files = os.listdir(base_dir)

# Moves all training cat images to cats folder, training dog images to dogs folder
def train_maker(name):
  try:
      path = f"{base_dir}/train/{name}"
      os.makedirs(path, exist_ok=True)
  except OSError:
      print ("Creation of the directory failed")
  else:
      print ("Successfully created the directory")
  print("here")
  train_dir = f"{base_dir}/train/{name}"
  print(train_dir)
  files = os.listdir(dataset_dir)
  print(files)
  
  for f in files:
        search_object = re.search(name.lower(), f)
        print(search_object)
        if search_object:
          shutil.move(f'{dataset_dir}/{f}', train_dir)

train_maker("lion")
train_maker("tiger")
train_maker("cow")
Successfully created the directory %s 
Successfully created the directory
here
PetImages/train/lion
['cow_315.jpg', 'lion_257.jpg', 'cow_145.jpg', 'tiger_407.jpg', 'tiger_7.jpg', 'lion_37.jpg', 'cow_221.jpg', 'lion_455.jpg', 'tiger_267.jpg', 'lion_239.jpg', 'tiger_396.jpg', 'lion_10.jpg', 'lion_271.jpg', 'tiger_38.jpg', 'cow_334.jpg', 'lion_147.jpg', 'lion_61.jpg', 'tiger_219.jpg', 'tiger_238.jpg', 'cow_403.jpg', 'cow_59.jpg', 'lion_276.jpg', 'lion_36.jpg', 'lion_243.jpg', 'tiger_304.jpg', 'cow_32.jpg', 'tiger_23.jpg', 'lion_66.jpg', 'tiger_155.jpg', 'lion_225.jpg', 'cow_235.jpg', 'cow_69.jpg', 'lion_286.jpg', 'lion_162.jpg', 'lion_349.jpg', 'lion_12.jpg', 'cow_163.jpg', 'tiger_198.jpg', 'cow_118.jpg', 'lion_99.jpg', 'cow_11.jpg', 'lion_71.jpg', 'cow_250.jpg', 'lion_339.jpg', 'cow_114.jpg', 'tiger_78.jpg', 'lion_329.jpg', 'lion_459.jpg', 'lion_410.jpg', 'tiger_201.jpg', 'cow_43.jpg', 'tiger_118.jpg', 'tiger_269.jpg', 'cow_426.jpg', 'tiger_170.jpg', 'tiger_315.jpg', 'tiger_176.jpg', 'lion_298.jpg', 'cow_252.jpg', 'cow_49.jpg', 'lion_181.jpg', 'tiger_409.jpg', 'lion_312.jpg', 'lion_92.jpg', 'lion_207.jpg', 'tiger_262.jpg', 'cow_63.jpg', 'lion_39.jpg', 'tiger_56.jpg', 'lion_127.jpg', 'lion_413.jpg', 'tiger_316.jpg', 'lion_230.jpg', 'lion_112.jpg', 'tiger_283.jpg', 'cow_217.jpg', 'tiger_378.jpg', 'lion_83.jpg', 'tiger_42.jpg', 'cow_174.jpg', 'lion_371.jpg', 'cow_344.jpg', 'lion_321.jpg', 'lion_354.jpg', 'tiger_187.jpg', 'cow_184.jpg', 'lion_191.jpg', 'lion_255.jpg', 'tiger_395.jpg', 'lion_60.jpg', 'lion_274.jpg', 'cow_97.jpg', 'cow_314.jpg', 'cow_139.jpg', 'lion_391.jpg', 'lion_90.jpg', 'cow_366.jpg', 'tiger_297.jpg', 'tiger_79.jpg', 'lion_429.jpg', 'tiger_209.jpg', 'lion_268.jpg', 'cow_100.jpg', 'lion_164.jpg', 'tiger_335.jpg', 'tiger_224.jpg', 'tiger_31.jpg', 'tiger_311.jpg', 'lion_362.jpg', 'lion_379.jpg', 'cow_229.jpg', 'cow_309.jpg', 'tiger_228.jpg', 'lion_17.jpg', 'tiger_142.jpg', 'lion_220.jpg', 'cow_419.jpg', 'tiger_253.jpg', 'lion_355.jpg', 'lion_222.jpg', 'cow_89.jpg', 'lion_205.jpg', 'tiger_185.jpg', 'cow_360.jpg', 'lion_105.jpg', 'lion_82.jpg', 'lion_101.jpg', 'cow_151.jpg', 'lion_287.jpg', 'lion_364.jpg', 'tiger_399.jpg', 'lion_219.jpg', 'cow_337.jpg', 'cow_78.jpg', 'lion_381.jpg', 'tiger_205.jpg', 'tiger_256.jpg', 'tiger_353.jpg', 'cow_374.jpg', 'lion_411.jpg', 'cow_304.jpg', 'cow_214.jpg', 'cow_200.jpg', 'tiger_141.jpg', 'tiger_91.jpg', 'tiger_217.jpg', 'lion_131.jpg', 'tiger_179.jpg', 'tiger_216.jpg', 'tiger_13.jpg', 'lion_166.jpg', 'lion_284.jpg', 'lion_285.jpg', 'lion_217.jpg', 'cow_293.jpg', 'tiger_15.jpg', 'cow_178.jpg', 'tiger_66.jpg', 'tiger_417.jpg', 'tiger_58.jpg', 'lion_129.jpg', 'tiger_367.jpg', 'tiger_145.jpg', 'lion_293.jpg', 'cow_286.jpg', 'cow_166.jpg', 'cow_36.jpg', 'cow_142.jpg', 'cow_263.jpg', 'cow_312.jpg', 'lion_224.jpg', 'cow_288.jpg', 'tiger_332.jpg', 'lion_236.jpg', 'lion_152.jpg', 'lion_41.jpg', 'lion_302.jpg', 'cow_179.jpg', 'tiger_370.jpg', 'cow_434.jpg', 'lion_368.jpg', 'tiger_152.jpg', 'lion_51.jpg', 'tiger_250.jpg', 'tiger_215.jpg', 'lion_43.jpg', 'cow_48.jpg', 'tiger_45.jpg', 'tiger_346.jpg', 'tiger_47.jpg', 'cow_228.jpg', 'tiger_173.jpg', 'cow_354.jpg', 'lion_353.jpg', 'cow_121.jpg', 'tiger_206.jpg', 'cow_72.jpg', 'tiger_203.jpg', 'lion_55.jpg', 'lion_132.jpg', 'cow_220.jpg', 'tiger_104.jpg', 'cow_149.jpg', 'lion_44.jpg', 'tiger_360.jpg', 'tiger_365.jpg', 'tiger_105.jpg', 'cow_427.jpg', 'cow_55.jpg', 'cow_267.jpg', 'lion_425.jpg', 'lion_176.jpg', 'cow_202.jpg', 'tiger_183.jpg', 'cow_167.jpg', 'tiger_90.jpg', 'tiger_110.jpg', 'tiger_197.jpg', 'cow_383.jpg', 'lion_350.jpg', 'cow_209.jpg', 'tiger_88.jpg', 'lion_246.jpg', 'cow_115.jpg', 'lion_175.jpg', 'cow_297.jpg', 'cow_14.jpg', 'tiger_279.jpg', 'cow_244.jpg', 'tiger_403.jpg', 'cow_317.jpg', 'tiger_64.jpg', 'tiger_222.jpg', 'tiger_294.jpg', 'tiger_225.jpg', 'lion_42.jpg', 'cow_61.jpg', 'lion_218.jpg', 'cow_111.jpg', 'lion_153.jpg', 'lion_407.jpg', 'lion_348.jpg', 'cow_194.jpg', 'tiger_271.jpg', 'lion_68.jpg', 'lion_326.jpg', 'cow_165.jpg', 'lion_171.jpg', 'cow_416.jpg', 'lion_9.jpg', 'cow_20.jpg', 'cow_152.jpg', 'tiger_89.jpg', 'cow_108.jpg', 'lion_428.jpg', 'cow_261.jpg', 'tiger_371.jpg', 'lion_100.jpg', 'cow_148.jpg', 'tiger_48.jpg', 'lion_344.jpg', 'cow_25.jpg', 'cow_258.jpg', 'lion_404.jpg', 'cow_256.jpg', 'lion_201.jpg', 'tiger_300.jpg', 'cow_210.jpg', 'tiger_124.jpg', 'cow_132.jpg', 'cow_238.jpg', 'tiger_52.jpg', 'tiger_29.jpg', 'tiger_348.jpg', 'tiger_212.jpg', 'lion_126.jpg', 'cow_86.jpg', 'cow_376.jpg', 'tiger_107.jpg', 'tiger_277.jpg', 'lion_318.jpg', 'tiger_257.jpg', 'cow_440.jpg', 'lion_385.jpg', 'tiger_349.jpg', 'lion_357.jpg', 'tiger_241.jpg', 'lion_87.jpg', 'tiger_251.jpg', 'tiger_412.jpg', 'cow_237.jpg', 'lion_461.jpg', 'cow_222.jpg', 'cow_239.jpg', 'lion_57.jpg', 'lion_149.jpg', 'tiger_200.jpg', 'cow_291.jpg', 'cow_373.jpg', 'cow_76.jpg', 'lion_408.jpg', 'tiger_314.jpg', 'tiger_165.jpg', 'cow_285.jpg', 'cow_402.jpg', 'lion_137.jpg', 'lion_103.jpg', 'tiger_154.jpg', 'tiger_296.jpg', 'lion_53.jpg', 'lion_259.jpg', 'tiger_9.jpg', 'lion_79.jpg', 'tiger_324.jpg', 'lion_278.jpg', 'tiger_352.jpg', 'tiger_373.jpg', 'lion_377.jpg', 'cow_336.jpg', 'cow_423.jpg', 'tiger_131.jpg', 'cow_280.jpg', 'tiger_8.jpg', 'cow_357.jpg', 'cow_385.jpg', 'lion_144.jpg', 'tiger_207.jpg', 'tiger_69.jpg', 'lion_161.jpg', 'lion_358.jpg', 'cow_219.jpg', 'lion_267.jpg', 'tiger_285.jpg', 'tiger_190.jpg', 'cow_311.jpg', 'tiger_345.jpg', 'tiger_70.jpg', 'tiger_184.jpg', 'tiger_343.jpg', 'tiger_16.jpg', 'lion_108.jpg', 'cow_18.jpg', 'lion_442.jpg', 'cow_247.jpg', 'lion_226.jpg', 'tiger_221.jpg', 'tiger_278.jpg', 'tiger_280.jpg', 'lion_288.jpg', 'cow_50.jpg', 'tiger_312.jpg', 'lion_85.jpg', 'lion_199.jpg', 'lion_134.jpg', 'lion_84.jpg', 'tiger_75.jpg', 'lion_396.jpg', 'tiger_208.jpg', 'cow_207.jpg', 'cow_211.jpg', 'cow_52.jpg', 'cow_120.jpg', 'lion_125.jpg', 'cow_73.jpg', 'lion_23.jpg', 'lion_110.jpg', 'cow_58.jpg', 'lion_453.jpg', 'lion_209.jpg', 'lion_366.jpg', 'tiger_401.jpg', 'lion_124.jpg', 'tiger_135.jpg', 'cow_397.jpg', 'cow_82.jpg', 'lion_440.jpg', 'lion_155.jpg', 'cow_332.jpg', 'cow_224.jpg', 'tiger_138.jpg', 'cow_230.jpg', 'cow_313.jpg', 'tiger_65.jpg', 'tiger_134.jpg', 'lion_322.jpg', 'lion_352.jpg', 'tiger_116.jpg', 'cow_225.jpg', 'cow_128.jpg', 'tiger_112.jpg', 'tiger_379.jpg', 'lion_107.jpg', 'cow_30.jpg', 'cow_318.jpg', 'tiger_80.jpg', 'tiger_218.jpg', 'tiger_340.jpg', 'tiger_355.jpg', 'cow_298.jpg', 'lion_296.jpg', 'tiger_266.jpg', 'cow_6.jpg', 'cow_124.jpg', 'lion_19.jpg', 'cow_56.jpg', 'cow_134.jpg', 'tiger_204.jpg', 'lion_106.jpg', 'cow_16.jpg', 'tiger_413.jpg', 'lion_264.jpg', 'tiger_199.jpg', 'tiger_181.jpg', 'cow_106.jpg', 'cow_290.jpg', 'cow_135.jpg', 'cow_232.jpg', 'cow_190.jpg', 'cow_23.jpg', 'lion_172.jpg', 'tiger_191.jpg', 'lion_62.jpg', 'tiger_125.jpg', 'tiger_282.jpg', 'cow_351.jpg', 'cow_189.jpg', 'tiger_92.jpg', 'lion_454.jpg', 'tiger_132.jpg', 'tiger_77.jpg', 'cow_13.jpg', 'lion_443.jpg', 'cow_146.jpg', 'tiger_383.jpg', 'cow_197.jpg', 'cow_399.jpg', 'tiger_368.jpg', 'cow_405.jpg', 'tiger_227.jpg', 'cow_162.jpg', 'lion_203.jpg', 'cow_112.jpg', 'lion_154.jpg', 'lion_143.jpg', 'tiger_372.jpg', 'cow_352.jpg', 'lion_128.jpg', 'cow_382.jpg', 'cow_104.jpg', 'lion_245.jpg', 'tiger_148.jpg', 'lion_361.jpg', 'lion_451.jpg', 'cow_412.jpg', 'lion_182.jpg', 'lion_231.jpg', 'tiger_94.jpg', 'tiger_308.jpg', 'lion_98.jpg', 'lion_16.jpg', 'cow_212.jpg', 'lion_77.jpg', 'tiger_32.jpg', 'cow_236.jpg', 'lion_133.jpg', 'cow_307.jpg', 'tiger_55.jpg', 'cow_66.jpg', 'tiger_415.jpg', 'lion_380.jpg', 'lion_148.jpg', 'lion_295.jpg', 'tiger_186.jpg', 'tiger_59.jpg', 'tiger_123.jpg', 'tiger_6.jpg', 'lion_174.jpg', 'tiger_151.jpg', 'cow_172.jpg', 'lion_67.jpg', 'lion_228.jpg', 'lion_254.jpg', 'cow_302.jpg', 'lion_111.jpg', 'tiger_143.jpg', 'lion_261.jpg', 'lion_135.jpg', 'tiger_236.jpg', 'lion_168.jpg', 'lion_14.jpg', 'lion_297.jpg', 'lion_313.jpg', 'lion_356.jpg', 'cow_41.jpg', 'tiger_229.jpg', 'cow_338.jpg', 'lion_242.jpg', 'lion_146.jpg', 'tiger_248.jpg', 'lion_102.jpg', 'cow_203.jpg', 'lion_422.jpg', 'tiger_157.jpg', 'cow_196.jpg', 'cow_198.jpg', 'lion_420.jpg', 'lion_327.jpg', 'cow_262.jpg', 'cow_404.jpg', 'lion_369.jpg', 'tiger_74.jpg', 'tiger_249.jpg', 'tiger_136.jpg', 'tiger_404.jpg', 'lion_310.jpg', 'cow_284.jpg', 'cow_281.jpg', 'cow_415.jpg', 'cow_177.jpg', 'lion_346.jpg', 'tiger_67.jpg', 'lion_395.jpg', 'tiger_27.jpg', 'tiger_49.jpg', 'lion_193.jpg', 'cow_28.jpg', 'cow_129.jpg', 'tiger_22.jpg', 'tiger_109.jpg', 'tiger_240.jpg', 'cow_378.jpg', 'tiger_234.jpg', 'tiger_129.jpg', 'cow_10.jpg', 'tiger_19.jpg', 'lion_338.jpg', 'lion_54.jpg', 'lion_32.jpg', 'lion_86.jpg', 'cow_156.jpg', 'tiger_410.jpg', 'tiger_247.jpg', 'cow_421.jpg', 'tiger_351.jpg', 'lion_159.jpg', 'lion_240.jpg', 'lion_291.jpg', 'cow_64.jpg', 'tiger_245.jpg', 'cow_81.jpg', 'tiger_328.jpg', 'tiger_302.jpg', 'lion_194.jpg', 'tiger_376.jpg', 'cow_191.jpg', 'cow_375.jpg', 'lion_169.jpg', 'cow_248.jpg', 'lion_117.jpg', 'lion_158.jpg', 'tiger_121.jpg', 'cow_205.jpg', 'tiger_281.jpg', 'tiger_313.jpg', 'lion_417.jpg', 'lion_272.jpg', 'lion_347.jpg', 'cow_359.jpg', 'lion_258.jpg', 'cow_83.jpg', 'cow_316.jpg', 'lion_330.jpg', 'cow_295.jpg', 'lion_382.jpg', 'tiger_108.jpg', 'tiger_81.jpg', 'tiger_33.jpg', 'lion_393.jpg', 'lion_270.jpg', 'tiger_111.jpg', 'lion_76.jpg', 'cow_157.jpg', 'lion_13.jpg', 'tiger_153.jpg', 'cow_392.jpg', 'lion_141.jpg', 'lion_340.jpg', 'tiger_347.jpg', 'tiger_366.jpg', 'cow_245.jpg', 'tiger_113.jpg', 'cow_381.jpg', 'lion_177.jpg', 'tiger_159.jpg', 'lion_234.jpg', 'lion_332.jpg', 'cow_4.jpg', 'tiger_270.jpg', 'lion_388.jpg', 'cow_384.jpg', 'tiger_252.jpg', 'cow_159.jpg', 'cow_117.jpg', 'lion_292.jpg', 'cow_417.jpg', 'lion_73.jpg', 'cow_292.jpg', 'cow_169.jpg', 'lion_319.jpg', 'lion_446.jpg', 'tiger_140.jpg', 'tiger_72.jpg', 'cow_306.jpg', 'cow_29.jpg', 'tiger_168.jpg', 'tiger_419.jpg', 'tiger_275.jpg', 'lion_317.jpg', 'cow_39.jpg', 'tiger_272.jpg', 'tiger_53.jpg', 'cow_319.jpg', 'cow_113.jpg', 'tiger_128.jpg', 'tiger_317.jpg', 'lion_456.jpg', 'lion_445.jpg', 'cow_137.jpg', 'tiger_60.jpg', 'tiger_286.jpg', 'tiger_36.jpg', 'cow_70.jpg', 'lion_65.jpg', 'lion_253.jpg', 'lion_237.jpg', 'tiger_182.jpg', 'cow_87.jpg', 'cow_144.jpg', 'lion_74.jpg', 'lion_433.jpg', 'cow_175.jpg', 'tiger_174.jpg', 'lion_48.jpg', 'cow_47.jpg', 'lion_247.jpg', 'tiger_37.jpg', 'lion_403.jpg', 'tiger_115.jpg', 'cow_44.jpg', 'lion_150.jpg', 'cow_201.jpg', 'cow_171.jpg', 'cow_401.jpg', 'tiger_310.jpg', 'cow_255.jpg', 'cow_396.jpg', 'cow_259.jpg', 'tiger_188.jpg', 'cow_126.jpg', 'lion_200.jpg', 'cow_168.jpg', 'cow_119.jpg', 'lion_221.jpg', 'lion_431.jpg', 'cow_38.jpg', 'tiger_330.jpg', 'tiger_39.jpg', 'cow_380.jpg', 'tiger_333.jpg', 'tiger_133.jpg', 'lion_178.jpg', 'lion_448.jpg', 'lion_324.jpg', 'tiger_391.jpg', 'lion_303.jpg', 'lion_387.jpg', 'cow_377.jpg', 'tiger_363.jpg', 'lion_81.jpg', 'cow_99.jpg', 'cow_331.jpg', 'cow_294.jpg', 'tiger_295.jpg', 'lion_471.jpg', 'tiger_61.jpg', 'cow_279.jpg', 'lion_196.jpg', 'cow_79.jpg', 'tiger_144.jpg', 'cow_296.jpg', 'cow_226.jpg', 'cow_425.jpg', 'tiger_358.jpg', 'cow_17.jpg', 'tiger_119.jpg', 'lion_250.jpg', 'lion_35.jpg', 'cow_234.jpg', 'cow_204.jpg', 'lion_438.jpg', 'cow_27.jpg', 'cow_31.jpg', 'tiger_126.jpg', 'cow_37.jpg', 'lion_252.jpg', 'cow_265.jpg', 'tiger_26.jpg', 'lion_47.jpg', 'lion_248.jpg', 'cow_287.jpg', 'lion_316.jpg', 'tiger_149.jpg', 'lion_434.jpg', 'lion_140.jpg', 'lion_449.jpg', 'cow_45.jpg', 'cow_206.jpg', 'lion_323.jpg', 'cow_130.jpg', 'tiger_122.jpg', 'cow_154.jpg', 'tiger_406.jpg', 'lion_273.jpg', 'tiger_177.jpg', 'lion_56.jpg', 'tiger_416.jpg', 'cow_40.jpg', 'cow_216.jpg', 'tiger_220.jpg', 'lion_363.jpg', 'cow_333.jpg', 'tiger_344.jpg', 'cow_90.jpg', 'lion_426.jpg', 'cow_439.jpg', 'cow_300.jpg', 'lion_227.jpg', 'lion_192.jpg', 'tiger_307.jpg', 'tiger_397.jpg', 'lion_116.jpg', 'lion_458.jpg', 'cow_435.jpg', 'tiger_390.jpg', 'tiger_93.jpg', 'cow_443.jpg', 'lion_33.jpg', 'lion_416.jpg', 'tiger_382.jpg', 'cow_301.jpg', 'lion_8.jpg', 'lion_262.jpg', 'tiger_17.jpg', 'cow_241.jpg', 'tiger_103.jpg', 'lion_75.jpg', 'cow_84.jpg', 'tiger_411.jpg', 'cow_269.jpg', 'tiger_336.jpg', 'tiger_57.jpg', 'tiger_305.jpg', 'cow_107.jpg', 'lion_406.jpg', 'cow_131.jpg', 'tiger_169.jpg', 'cow_278.jpg', 'tiger_375.jpg', 'cow_249.jpg', 'cow_441.jpg', 'lion_447.jpg', 'lion_345.jpg', 'tiger_84.jpg', 'cow_173.jpg', 'lion_265.jpg', 'tiger_189.jpg', 'tiger_166.jpg', 'cow_46.jpg', 'cow_110.jpg', 'lion_7.jpg', 'cow_356.jpg', 'cow_68.jpg', 'cow_342.jpg', 'cow_80.jpg', 'lion_335.jpg', 'cow_26.jpg', 'lion_59.jpg', 'tiger_258.jpg', 'tiger_156.jpg', 'tiger_160.jpg', 'cow_186.jpg', 'cow_133.jpg', 'lion_419.jpg', 'cow_103.jpg', 'cow_340.jpg', 'cow_400.jpg', 'lion_198.jpg', 'lion_202.jpg', 'tiger_40.jpg', 'lion_64.jpg', 'tiger_232.jpg', 'lion_378.jpg', 'lion_389.jpg', 'tiger_5.jpg', 'tiger_327.jpg', 'tiger_321.jpg', 'lion_5.jpg', 'tiger_369.jpg', 'cow_7.jpg', 'cow_9.jpg', 'cow_243.jpg', 'lion_462.jpg', 'lion_157.jpg', 'cow_266.jpg', 'lion_289.jpg', 'cow_270.jpg', 'lion_256.jpg', 'tiger_414.jpg', 'tiger_223.jpg', 'tiger_86.jpg', 'cow_62.jpg', 'cow_42.jpg', 'cow_88.jpg', 'cow_170.jpg', 'lion_437.jpg', 'tiger_326.jpg', 'tiger_259.jpg', 'lion_336.jpg', 'lion_78.jpg', 'cow_355.jpg', 'lion_334.jpg', 'lion_470.jpg', 'lion_365.jpg', 'lion_45.jpg', 'cow_22.jpg', 'cow_343.jpg', 'tiger_323.jpg', 'tiger_334.jpg', 'tiger_162.jpg', 'lion_18.jpg', 'tiger_14.jpg', 'lion_412.jpg', 'tiger_230.jpg', 'cow_444.jpg', 'tiger_393.jpg', 'lion_405.jpg', 'tiger_82.jpg', 'tiger_46.jpg', 'tiger_255.jpg', 'tiger_161.jpg', 'tiger_276.jpg', 'tiger_237.jpg', 'cow_94.jpg', 'lion_6.jpg', 'cow_34.jpg', 'lion_333.jpg', 'cow_424.jpg', 'lion_210.jpg', 'tiger_178.jpg', 'cow_442.jpg', 'cow_122.jpg', 'cow_268.jpg', 'lion_444.jpg', 'cow_438.jpg', 'lion_109.jpg', 'tiger_261.jpg', 'tiger_44.jpg', 'lion_223.jpg', 'tiger_362.jpg', 'tiger_30.jpg', 'lion_136.jpg', 'cow_353.jpg', 'lion_390.jpg', 'tiger_239.jpg', 'cow_246.jpg', 'tiger_24.jpg', 'lion_130.jpg', 'cow_394.jpg', 'cow_218.jpg', 'tiger_299.jpg', 'tiger_101.jpg', 'cow_322.jpg', 'cow_254.jpg', 'cow_188.jpg', 'cow_223.jpg', 'cow_57.jpg', 'cow_242.jpg', 'lion_170.jpg', 'lion_457.jpg', 'lion_351.jpg', 'lion_72.jpg', 'tiger_87.jpg', 'lion_263.jpg', 'tiger_320.jpg', 'lion_15.jpg', 'cow_277.jpg', 'tiger_211.jpg', 'tiger_381.jpg', 'cow_21.jpg', 'cow_136.jpg', 'cow_253.jpg', 'cow_257.jpg', 'tiger_319.jpg', 'tiger_377.jpg', 'lion_34.jpg', 'cow_160.jpg', 'cow_260.jpg', 'lion_300.jpg', 'cow_98.jpg', 'cow_140.jpg', 'tiger_231.jpg', 'cow_176.jpg', 'lion_427.jpg', 'tiger_127.jpg', 'lion_436.jpg', 'tiger_301.jpg', 'tiger_171.jpg', 'lion_24.jpg', 'cow_208.jpg', 'tiger_392.jpg', 'tiger_25.jpg', 'tiger_175.jpg', 'cow_75.jpg', 'tiger_20.jpg', 'cow_164.jpg', 'cow_358.jpg', 'cow_364.jpg', 'tiger_325.jpg', 'lion_165.jpg', 'tiger_264.jpg', 'tiger_273.jpg', 'cow_264.jpg', 'cow_180.jpg', 'tiger_354.jpg', 'cow_138.jpg', 'cow_74.jpg', 'cow_276.jpg', 'cow_158.jpg', 'tiger_35.jpg', 'cow_96.jpg', 'tiger_400.jpg', 'lion_163.jpg', 'tiger_95.jpg', 'lion_260.jpg', 'tiger_120.jpg', 'tiger_337.jpg', 'tiger_63.jpg', 'lion_314.jpg', 'tiger_274.jpg', 'tiger_102.jpg', 'tiger_83.jpg', 'tiger_303.jpg', 'cow_8.jpg', 'tiger_408.jpg', 'lion_441.jpg', 'lion_195.jpg', 'cow_147.jpg', 'lion_460.jpg', 'cow_127.jpg', 'cow_436.jpg', 'tiger_163.jpg', 'lion_40.jpg', 'lion_311.jpg', 'tiger_341.jpg', 'cow_187.jpg', 'tiger_28.jpg', 'cow_116.jpg', 'lion_423.jpg', 'lion_241.jpg', 'cow_67.jpg', 'tiger_318.jpg', 'tiger_293.jpg', 'tiger_389.jpg', 'tiger_244.jpg', 'lion_439.jpg', 'cow_227.jpg', 'cow_320.jpg', 'tiger_357.jpg', 'tiger_11.jpg', 'lion_386.jpg', 'cow_391.jpg', 'lion_69.jpg', 'cow_274.jpg', 'tiger_398.jpg', 'lion_180.jpg', 'tiger_85.jpg', 'tiger_180.jpg', 'cow_101.jpg', 'lion_183.jpg', 'cow_193.jpg', 'cow_153.jpg', 'lion_233.jpg', 'lion_343.jpg', 'cow_283.jpg', 'lion_367.jpg', 'lion_38.jpg', 'tiger_12.jpg', 'tiger_214.jpg']
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
None
<re.Match object; span=(0, 4), match='lion'>
None
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
<re.Match object; span=(0, 4), match='lion'>
<re.Match object; span=(0, 4), match='lion'>
None
None
Successfully created the directory
here
PetImages/train/tiger
['cow_315.jpg', 'cow_145.jpg', 'tiger_407.jpg', 'tiger_7.jpg', 'cow_221.jpg', 'tiger_267.jpg', 'tiger_396.jpg', 'tiger_38.jpg', 'cow_334.jpg', 'tiger_219.jpg', 'tiger_238.jpg', 'cow_403.jpg', 'cow_59.jpg', 'tiger_304.jpg', 'cow_32.jpg', 'tiger_23.jpg', 'tiger_155.jpg', 'cow_235.jpg', 'cow_69.jpg', 'cow_163.jpg', 'tiger_198.jpg', 'cow_118.jpg', 'cow_11.jpg', 'cow_250.jpg', 'cow_114.jpg', 'tiger_78.jpg', 'tiger_201.jpg', 'cow_43.jpg', 'tiger_118.jpg', 'tiger_269.jpg', 'cow_426.jpg', 'tiger_170.jpg', 'tiger_315.jpg', 'tiger_176.jpg', 'cow_252.jpg', 'cow_49.jpg', 'tiger_409.jpg', 'tiger_262.jpg', 'cow_63.jpg', 'tiger_56.jpg', 'tiger_316.jpg', 'tiger_283.jpg', 'cow_217.jpg', 'tiger_378.jpg', 'tiger_42.jpg', 'cow_174.jpg', 'cow_344.jpg', 'tiger_187.jpg', 'cow_184.jpg', 'tiger_395.jpg', 'cow_97.jpg', 'cow_314.jpg', 'cow_139.jpg', 'cow_366.jpg', 'tiger_297.jpg', 'tiger_79.jpg', 'tiger_209.jpg', 'cow_100.jpg', 'tiger_335.jpg', 'tiger_224.jpg', 'tiger_31.jpg', 'tiger_311.jpg', 'cow_229.jpg', 'cow_309.jpg', 'tiger_228.jpg', 'tiger_142.jpg', 'cow_419.jpg', 'tiger_253.jpg', 'cow_89.jpg', 'tiger_185.jpg', 'cow_360.jpg', 'cow_151.jpg', 'tiger_399.jpg', 'cow_337.jpg', 'cow_78.jpg', 'tiger_205.jpg', 'tiger_256.jpg', 'tiger_353.jpg', 'cow_374.jpg', 'cow_304.jpg', 'cow_214.jpg', 'cow_200.jpg', 'tiger_141.jpg', 'tiger_91.jpg', 'tiger_217.jpg', 'tiger_179.jpg', 'tiger_216.jpg', 'tiger_13.jpg', 'cow_293.jpg', 'tiger_15.jpg', 'cow_178.jpg', 'tiger_66.jpg', 'tiger_417.jpg', 'tiger_58.jpg', 'tiger_367.jpg', 'tiger_145.jpg', 'cow_286.jpg', 'cow_166.jpg', 'cow_36.jpg', 'cow_142.jpg', 'cow_263.jpg', 'cow_312.jpg', 'cow_288.jpg', 'tiger_332.jpg', 'cow_179.jpg', 'tiger_370.jpg', 'cow_434.jpg', 'tiger_152.jpg', 'tiger_250.jpg', 'tiger_215.jpg', 'cow_48.jpg', 'tiger_45.jpg', 'tiger_346.jpg', 'tiger_47.jpg', 'cow_228.jpg', 'tiger_173.jpg', 'cow_354.jpg', 'cow_121.jpg', 'tiger_206.jpg', 'cow_72.jpg', 'tiger_203.jpg', 'cow_220.jpg', 'tiger_104.jpg', 'cow_149.jpg', 'tiger_360.jpg', 'tiger_365.jpg', 'tiger_105.jpg', 'cow_427.jpg', 'cow_55.jpg', 'cow_267.jpg', 'cow_202.jpg', 'tiger_183.jpg', 'cow_167.jpg', 'tiger_90.jpg', 'tiger_110.jpg', 'tiger_197.jpg', 'cow_383.jpg', 'cow_209.jpg', 'tiger_88.jpg', 'cow_115.jpg', 'cow_297.jpg', 'cow_14.jpg', 'tiger_279.jpg', 'cow_244.jpg', 'tiger_403.jpg', 'cow_317.jpg', 'tiger_64.jpg', 'tiger_222.jpg', 'tiger_294.jpg', 'tiger_225.jpg', 'cow_61.jpg', 'cow_111.jpg', 'cow_194.jpg', 'tiger_271.jpg', 'cow_165.jpg', 'cow_416.jpg', 'cow_20.jpg', 'cow_152.jpg', 'tiger_89.jpg', 'cow_108.jpg', 'cow_261.jpg', 'tiger_371.jpg', 'cow_148.jpg', 'tiger_48.jpg', 'cow_25.jpg', 'cow_258.jpg', 'cow_256.jpg', 'tiger_300.jpg', 'cow_210.jpg', 'tiger_124.jpg', 'cow_132.jpg', 'cow_238.jpg', 'tiger_52.jpg', 'tiger_29.jpg', 'tiger_348.jpg', 'tiger_212.jpg', 'cow_86.jpg', 'cow_376.jpg', 'tiger_107.jpg', 'tiger_277.jpg', 'tiger_257.jpg', 'cow_440.jpg', 'tiger_349.jpg', 'tiger_241.jpg', 'tiger_251.jpg', 'tiger_412.jpg', 'cow_237.jpg', 'cow_222.jpg', 'cow_239.jpg', 'tiger_200.jpg', 'cow_291.jpg', 'cow_373.jpg', 'cow_76.jpg', 'tiger_314.jpg', 'tiger_165.jpg', 'cow_285.jpg', 'cow_402.jpg', 'tiger_154.jpg', 'tiger_296.jpg', 'tiger_9.jpg', 'tiger_324.jpg', 'tiger_352.jpg', 'tiger_373.jpg', 'cow_336.jpg', 'cow_423.jpg', 'tiger_131.jpg', 'cow_280.jpg', 'tiger_8.jpg', 'cow_357.jpg', 'cow_385.jpg', 'tiger_207.jpg', 'tiger_69.jpg', 'cow_219.jpg', 'tiger_285.jpg', 'tiger_190.jpg', 'cow_311.jpg', 'tiger_345.jpg', 'tiger_70.jpg', 'tiger_184.jpg', 'tiger_343.jpg', 'tiger_16.jpg', 'cow_18.jpg', 'cow_247.jpg', 'tiger_221.jpg', 'tiger_278.jpg', 'tiger_280.jpg', 'cow_50.jpg', 'tiger_312.jpg', 'tiger_75.jpg', 'tiger_208.jpg', 'cow_207.jpg', 'cow_211.jpg', 'cow_52.jpg', 'cow_120.jpg', 'cow_73.jpg', 'cow_58.jpg', 'tiger_401.jpg', 'tiger_135.jpg', 'cow_397.jpg', 'cow_82.jpg', 'cow_332.jpg', 'cow_224.jpg', 'tiger_138.jpg', 'cow_230.jpg', 'cow_313.jpg', 'tiger_65.jpg', 'tiger_134.jpg', 'tiger_116.jpg', 'cow_225.jpg', 'cow_128.jpg', 'tiger_112.jpg', 'tiger_379.jpg', 'cow_30.jpg', 'cow_318.jpg', 'tiger_80.jpg', 'tiger_218.jpg', 'tiger_340.jpg', 'tiger_355.jpg', 'cow_298.jpg', 'tiger_266.jpg', 'cow_6.jpg', 'cow_124.jpg', 'cow_56.jpg', 'cow_134.jpg', 'tiger_204.jpg', 'cow_16.jpg', 'tiger_413.jpg', 'tiger_199.jpg', 'tiger_181.jpg', 'cow_106.jpg', 'cow_290.jpg', 'cow_135.jpg', 'cow_232.jpg', 'cow_190.jpg', 'cow_23.jpg', 'tiger_191.jpg', 'tiger_125.jpg', 'tiger_282.jpg', 'cow_351.jpg', 'cow_189.jpg', 'tiger_92.jpg', 'tiger_132.jpg', 'tiger_77.jpg', 'cow_13.jpg', 'cow_146.jpg', 'tiger_383.jpg', 'cow_197.jpg', 'cow_399.jpg', 'tiger_368.jpg', 'cow_405.jpg', 'tiger_227.jpg', 'cow_162.jpg', 'cow_112.jpg', 'tiger_372.jpg', 'cow_352.jpg', 'cow_382.jpg', 'cow_104.jpg', 'tiger_148.jpg', 'cow_412.jpg', 'tiger_94.jpg', 'tiger_308.jpg', 'cow_212.jpg', 'tiger_32.jpg', 'cow_236.jpg', 'cow_307.jpg', 'tiger_55.jpg', 'cow_66.jpg', 'tiger_415.jpg', 'tiger_186.jpg', 'tiger_59.jpg', 'tiger_123.jpg', 'tiger_6.jpg', 'tiger_151.jpg', 'cow_172.jpg', 'cow_302.jpg', 'tiger_143.jpg', 'tiger_236.jpg', 'cow_41.jpg', 'tiger_229.jpg', 'cow_338.jpg', 'tiger_248.jpg', 'cow_203.jpg', 'tiger_157.jpg', 'cow_196.jpg', 'cow_198.jpg', 'cow_262.jpg', 'cow_404.jpg', 'tiger_74.jpg', 'tiger_249.jpg', 'tiger_136.jpg', 'tiger_404.jpg', 'cow_284.jpg', 'cow_281.jpg', 'cow_415.jpg', 'cow_177.jpg', 'tiger_67.jpg', 'tiger_27.jpg', 'tiger_49.jpg', 'cow_28.jpg', 'cow_129.jpg', 'tiger_22.jpg', 'tiger_109.jpg', 'tiger_240.jpg', 'cow_378.jpg', 'tiger_234.jpg', 'tiger_129.jpg', 'cow_10.jpg', 'tiger_19.jpg', 'cow_156.jpg', 'tiger_410.jpg', 'tiger_247.jpg', 'cow_421.jpg', 'tiger_351.jpg', 'cow_64.jpg', 'tiger_245.jpg', 'cow_81.jpg', 'tiger_328.jpg', 'tiger_302.jpg', 'tiger_376.jpg', 'cow_191.jpg', 'cow_375.jpg', 'cow_248.jpg', 'tiger_121.jpg', 'cow_205.jpg', 'tiger_281.jpg', 'tiger_313.jpg', 'cow_359.jpg', 'cow_83.jpg', 'cow_316.jpg', 'cow_295.jpg', 'tiger_108.jpg', 'tiger_81.jpg', 'tiger_33.jpg', 'tiger_111.jpg', 'cow_157.jpg', 'tiger_153.jpg', 'cow_392.jpg', 'tiger_347.jpg', 'tiger_366.jpg', 'cow_245.jpg', 'tiger_113.jpg', 'cow_381.jpg', 'tiger_159.jpg', 'cow_4.jpg', 'tiger_270.jpg', 'cow_384.jpg', 'tiger_252.jpg', 'cow_159.jpg', 'cow_117.jpg', 'cow_417.jpg', 'cow_292.jpg', 'cow_169.jpg', 'tiger_140.jpg', 'tiger_72.jpg', 'cow_306.jpg', 'cow_29.jpg', 'tiger_168.jpg', 'tiger_419.jpg', 'tiger_275.jpg', 'cow_39.jpg', 'tiger_272.jpg', 'tiger_53.jpg', 'cow_319.jpg', 'cow_113.jpg', 'tiger_128.jpg', 'tiger_317.jpg', 'cow_137.jpg', 'tiger_60.jpg', 'tiger_286.jpg', 'tiger_36.jpg', 'cow_70.jpg', 'tiger_182.jpg', 'cow_87.jpg', 'cow_144.jpg', 'cow_175.jpg', 'tiger_174.jpg', 'cow_47.jpg', 'tiger_37.jpg', 'tiger_115.jpg', 'cow_44.jpg', 'cow_201.jpg', 'cow_171.jpg', 'cow_401.jpg', 'tiger_310.jpg', 'cow_255.jpg', 'cow_396.jpg', 'cow_259.jpg', 'tiger_188.jpg', 'cow_126.jpg', 'cow_168.jpg', 'cow_119.jpg', 'cow_38.jpg', 'tiger_330.jpg', 'tiger_39.jpg', 'cow_380.jpg', 'tiger_333.jpg', 'tiger_133.jpg', 'tiger_391.jpg', 'cow_377.jpg', 'tiger_363.jpg', 'cow_99.jpg', 'cow_331.jpg', 'cow_294.jpg', 'tiger_295.jpg', 'tiger_61.jpg', 'cow_279.jpg', 'cow_79.jpg', 'tiger_144.jpg', 'cow_296.jpg', 'cow_226.jpg', 'cow_425.jpg', 'tiger_358.jpg', 'cow_17.jpg', 'tiger_119.jpg', 'cow_234.jpg', 'cow_204.jpg', 'cow_27.jpg', 'cow_31.jpg', 'tiger_126.jpg', 'cow_37.jpg', 'cow_265.jpg', 'tiger_26.jpg', 'cow_287.jpg', 'tiger_149.jpg', 'cow_45.jpg', 'cow_206.jpg', 'cow_130.jpg', 'tiger_122.jpg', 'cow_154.jpg', 'tiger_406.jpg', 'tiger_177.jpg', 'tiger_416.jpg', 'cow_40.jpg', 'cow_216.jpg', 'tiger_220.jpg', 'cow_333.jpg', 'tiger_344.jpg', 'cow_90.jpg', 'cow_439.jpg', 'cow_300.jpg', 'tiger_307.jpg', 'tiger_397.jpg', 'cow_435.jpg', 'tiger_390.jpg', 'tiger_93.jpg', 'cow_443.jpg', 'tiger_382.jpg', 'cow_301.jpg', 'tiger_17.jpg', 'cow_241.jpg', 'tiger_103.jpg', 'cow_84.jpg', 'tiger_411.jpg', 'cow_269.jpg', 'tiger_336.jpg', 'tiger_57.jpg', 'tiger_305.jpg', 'cow_107.jpg', 'cow_131.jpg', 'tiger_169.jpg', 'cow_278.jpg', 'tiger_375.jpg', 'cow_249.jpg', 'cow_441.jpg', 'tiger_84.jpg', 'cow_173.jpg', 'tiger_189.jpg', 'tiger_166.jpg', 'cow_46.jpg', 'cow_110.jpg', 'cow_356.jpg', 'cow_68.jpg', 'cow_342.jpg', 'cow_80.jpg', 'cow_26.jpg', 'tiger_258.jpg', 'tiger_156.jpg', 'tiger_160.jpg', 'cow_186.jpg', 'cow_133.jpg', 'cow_103.jpg', 'cow_340.jpg', 'cow_400.jpg', 'tiger_40.jpg', 'tiger_232.jpg', 'tiger_5.jpg', 'tiger_327.jpg', 'tiger_321.jpg', 'tiger_369.jpg', 'cow_7.jpg', 'cow_9.jpg', 'cow_243.jpg', 'cow_266.jpg', 'cow_270.jpg', 'tiger_414.jpg', 'tiger_223.jpg', 'tiger_86.jpg', 'cow_62.jpg', 'cow_42.jpg', 'cow_88.jpg', 'cow_170.jpg', 'tiger_326.jpg', 'tiger_259.jpg', 'cow_355.jpg', 'cow_22.jpg', 'cow_343.jpg', 'tiger_323.jpg', 'tiger_334.jpg', 'tiger_162.jpg', 'tiger_14.jpg', 'tiger_230.jpg', 'cow_444.jpg', 'tiger_393.jpg', 'tiger_82.jpg', 'tiger_46.jpg', 'tiger_255.jpg', 'tiger_161.jpg', 'tiger_276.jpg', 'tiger_237.jpg', 'cow_94.jpg', 'cow_34.jpg', 'cow_424.jpg', 'tiger_178.jpg', 'cow_442.jpg', 'cow_122.jpg', 'cow_268.jpg', 'cow_438.jpg', 'tiger_261.jpg', 'tiger_44.jpg', 'tiger_362.jpg', 'tiger_30.jpg', 'cow_353.jpg', 'tiger_239.jpg', 'cow_246.jpg', 'tiger_24.jpg', 'cow_394.jpg', 'cow_218.jpg', 'tiger_299.jpg', 'tiger_101.jpg', 'cow_322.jpg', 'cow_254.jpg', 'cow_188.jpg', 'cow_223.jpg', 'cow_57.jpg', 'cow_242.jpg', 'tiger_87.jpg', 'tiger_320.jpg', 'cow_277.jpg', 'tiger_211.jpg', 'tiger_381.jpg', 'cow_21.jpg', 'cow_136.jpg', 'cow_253.jpg', 'cow_257.jpg', 'tiger_319.jpg', 'tiger_377.jpg', 'cow_160.jpg', 'cow_260.jpg', 'cow_98.jpg', 'cow_140.jpg', 'tiger_231.jpg', 'cow_176.jpg', 'tiger_127.jpg', 'tiger_301.jpg', 'tiger_171.jpg', 'cow_208.jpg', 'tiger_392.jpg', 'tiger_25.jpg', 'tiger_175.jpg', 'cow_75.jpg', 'tiger_20.jpg', 'cow_164.jpg', 'cow_358.jpg', 'cow_364.jpg', 'tiger_325.jpg', 'tiger_264.jpg', 'tiger_273.jpg', 'cow_264.jpg', 'cow_180.jpg', 'tiger_354.jpg', 'cow_138.jpg', 'cow_74.jpg', 'cow_276.jpg', 'cow_158.jpg', 'tiger_35.jpg', 'cow_96.jpg', 'tiger_400.jpg', 'tiger_95.jpg', 'tiger_120.jpg', 'tiger_337.jpg', 'tiger_63.jpg', 'tiger_274.jpg', 'tiger_102.jpg', 'tiger_83.jpg', 'tiger_303.jpg', 'cow_8.jpg', 'tiger_408.jpg', 'cow_147.jpg', 'cow_127.jpg', 'cow_436.jpg', 'tiger_163.jpg', 'tiger_341.jpg', 'cow_187.jpg', 'tiger_28.jpg', 'cow_116.jpg', 'cow_67.jpg', 'tiger_318.jpg', 'tiger_293.jpg', 'tiger_389.jpg', 'tiger_244.jpg', 'cow_227.jpg', 'cow_320.jpg', 'tiger_357.jpg', 'tiger_11.jpg', 'cow_391.jpg', 'cow_274.jpg', 'tiger_398.jpg', 'tiger_85.jpg', 'tiger_180.jpg', 'cow_101.jpg', 'cow_193.jpg', 'cow_153.jpg', 'cow_283.jpg', 'tiger_12.jpg', 'tiger_214.jpg']
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
None
None
None
None
<re.Match object; span=(0, 5), match='tiger'>
<re.Match object; span=(0, 5), match='tiger'>
Successfully created the directory
here
PetImages/train/cow
['cow_315.jpg', 'cow_145.jpg', 'cow_221.jpg', 'cow_334.jpg', 'cow_403.jpg', 'cow_59.jpg', 'cow_32.jpg', 'cow_235.jpg', 'cow_69.jpg', 'cow_163.jpg', 'cow_118.jpg', 'cow_11.jpg', 'cow_250.jpg', 'cow_114.jpg', 'cow_43.jpg', 'cow_426.jpg', 'cow_252.jpg', 'cow_49.jpg', 'cow_63.jpg', 'cow_217.jpg', 'cow_174.jpg', 'cow_344.jpg', 'cow_184.jpg', 'cow_97.jpg', 'cow_314.jpg', 'cow_139.jpg', 'cow_366.jpg', 'cow_100.jpg', 'cow_229.jpg', 'cow_309.jpg', 'cow_419.jpg', 'cow_89.jpg', 'cow_360.jpg', 'cow_151.jpg', 'cow_337.jpg', 'cow_78.jpg', 'cow_374.jpg', 'cow_304.jpg', 'cow_214.jpg', 'cow_200.jpg', 'cow_293.jpg', 'cow_178.jpg', 'cow_286.jpg', 'cow_166.jpg', 'cow_36.jpg', 'cow_142.jpg', 'cow_263.jpg', 'cow_312.jpg', 'cow_288.jpg', 'cow_179.jpg', 'cow_434.jpg', 'cow_48.jpg', 'cow_228.jpg', 'cow_354.jpg', 'cow_121.jpg', 'cow_72.jpg', 'cow_220.jpg', 'cow_149.jpg', 'cow_427.jpg', 'cow_55.jpg', 'cow_267.jpg', 'cow_202.jpg', 'cow_167.jpg', 'cow_383.jpg', 'cow_209.jpg', 'cow_115.jpg', 'cow_297.jpg', 'cow_14.jpg', 'cow_244.jpg', 'cow_317.jpg', 'cow_61.jpg', 'cow_111.jpg', 'cow_194.jpg', 'cow_165.jpg', 'cow_416.jpg', 'cow_20.jpg', 'cow_152.jpg', 'cow_108.jpg', 'cow_261.jpg', 'cow_148.jpg', 'cow_25.jpg', 'cow_258.jpg', 'cow_256.jpg', 'cow_210.jpg', 'cow_132.jpg', 'cow_238.jpg', 'cow_86.jpg', 'cow_376.jpg', 'cow_440.jpg', 'cow_237.jpg', 'cow_222.jpg', 'cow_239.jpg', 'cow_291.jpg', 'cow_373.jpg', 'cow_76.jpg', 'cow_285.jpg', 'cow_402.jpg', 'cow_336.jpg', 'cow_423.jpg', 'cow_280.jpg', 'cow_357.jpg', 'cow_385.jpg', 'cow_219.jpg', 'cow_311.jpg', 'cow_18.jpg', 'cow_247.jpg', 'cow_50.jpg', 'cow_207.jpg', 'cow_211.jpg', 'cow_52.jpg', 'cow_120.jpg', 'cow_73.jpg', 'cow_58.jpg', 'cow_397.jpg', 'cow_82.jpg', 'cow_332.jpg', 'cow_224.jpg', 'cow_230.jpg', 'cow_313.jpg', 'cow_225.jpg', 'cow_128.jpg', 'cow_30.jpg', 'cow_318.jpg', 'cow_298.jpg', 'cow_6.jpg', 'cow_124.jpg', 'cow_56.jpg', 'cow_134.jpg', 'cow_16.jpg', 'cow_106.jpg', 'cow_290.jpg', 'cow_135.jpg', 'cow_232.jpg', 'cow_190.jpg', 'cow_23.jpg', 'cow_351.jpg', 'cow_189.jpg', 'cow_13.jpg', 'cow_146.jpg', 'cow_197.jpg', 'cow_399.jpg', 'cow_405.jpg', 'cow_162.jpg', 'cow_112.jpg', 'cow_352.jpg', 'cow_382.jpg', 'cow_104.jpg', 'cow_412.jpg', 'cow_212.jpg', 'cow_236.jpg', 'cow_307.jpg', 'cow_66.jpg', 'cow_172.jpg', 'cow_302.jpg', 'cow_41.jpg', 'cow_338.jpg', 'cow_203.jpg', 'cow_196.jpg', 'cow_198.jpg', 'cow_262.jpg', 'cow_404.jpg', 'cow_284.jpg', 'cow_281.jpg', 'cow_415.jpg', 'cow_177.jpg', 'cow_28.jpg', 'cow_129.jpg', 'cow_378.jpg', 'cow_10.jpg', 'cow_156.jpg', 'cow_421.jpg', 'cow_64.jpg', 'cow_81.jpg', 'cow_191.jpg', 'cow_375.jpg', 'cow_248.jpg', 'cow_205.jpg', 'cow_359.jpg', 'cow_83.jpg', 'cow_316.jpg', 'cow_295.jpg', 'cow_157.jpg', 'cow_392.jpg', 'cow_245.jpg', 'cow_381.jpg', 'cow_4.jpg', 'cow_384.jpg', 'cow_159.jpg', 'cow_117.jpg', 'cow_417.jpg', 'cow_292.jpg', 'cow_169.jpg', 'cow_306.jpg', 'cow_29.jpg', 'cow_39.jpg', 'cow_319.jpg', 'cow_113.jpg', 'cow_137.jpg', 'cow_70.jpg', 'cow_87.jpg', 'cow_144.jpg', 'cow_175.jpg', 'cow_47.jpg', 'cow_44.jpg', 'cow_201.jpg', 'cow_171.jpg', 'cow_401.jpg', 'cow_255.jpg', 'cow_396.jpg', 'cow_259.jpg', 'cow_126.jpg', 'cow_168.jpg', 'cow_119.jpg', 'cow_38.jpg', 'cow_380.jpg', 'cow_377.jpg', 'cow_99.jpg', 'cow_331.jpg', 'cow_294.jpg', 'cow_279.jpg', 'cow_79.jpg', 'cow_296.jpg', 'cow_226.jpg', 'cow_425.jpg', 'cow_17.jpg', 'cow_234.jpg', 'cow_204.jpg', 'cow_27.jpg', 'cow_31.jpg', 'cow_37.jpg', 'cow_265.jpg', 'cow_287.jpg', 'cow_45.jpg', 'cow_206.jpg', 'cow_130.jpg', 'cow_154.jpg', 'cow_40.jpg', 'cow_216.jpg', 'cow_333.jpg', 'cow_90.jpg', 'cow_439.jpg', 'cow_300.jpg', 'cow_435.jpg', 'cow_443.jpg', 'cow_301.jpg', 'cow_241.jpg', 'cow_84.jpg', 'cow_269.jpg', 'cow_107.jpg', 'cow_131.jpg', 'cow_278.jpg', 'cow_249.jpg', 'cow_441.jpg', 'cow_173.jpg', 'cow_46.jpg', 'cow_110.jpg', 'cow_356.jpg', 'cow_68.jpg', 'cow_342.jpg', 'cow_80.jpg', 'cow_26.jpg', 'cow_186.jpg', 'cow_133.jpg', 'cow_103.jpg', 'cow_340.jpg', 'cow_400.jpg', 'cow_7.jpg', 'cow_9.jpg', 'cow_243.jpg', 'cow_266.jpg', 'cow_270.jpg', 'cow_62.jpg', 'cow_42.jpg', 'cow_88.jpg', 'cow_170.jpg', 'cow_355.jpg', 'cow_22.jpg', 'cow_343.jpg', 'cow_444.jpg', 'cow_94.jpg', 'cow_34.jpg', 'cow_424.jpg', 'cow_442.jpg', 'cow_122.jpg', 'cow_268.jpg', 'cow_438.jpg', 'cow_353.jpg', 'cow_246.jpg', 'cow_394.jpg', 'cow_218.jpg', 'cow_322.jpg', 'cow_254.jpg', 'cow_188.jpg', 'cow_223.jpg', 'cow_57.jpg', 'cow_242.jpg', 'cow_277.jpg', 'cow_21.jpg', 'cow_136.jpg', 'cow_253.jpg', 'cow_257.jpg', 'cow_160.jpg', 'cow_260.jpg', 'cow_98.jpg', 'cow_140.jpg', 'cow_176.jpg', 'cow_208.jpg', 'cow_75.jpg', 'cow_164.jpg', 'cow_358.jpg', 'cow_364.jpg', 'cow_264.jpg', 'cow_180.jpg', 'cow_138.jpg', 'cow_74.jpg', 'cow_276.jpg', 'cow_158.jpg', 'cow_96.jpg', 'cow_8.jpg', 'cow_147.jpg', 'cow_127.jpg', 'cow_436.jpg', 'cow_187.jpg', 'cow_116.jpg', 'cow_67.jpg', 'cow_227.jpg', 'cow_320.jpg', 'cow_391.jpg', 'cow_274.jpg', 'cow_101.jpg', 'cow_193.jpg', 'cow_153.jpg', 'cow_283.jpg']
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
<re.Match object; span=(0, 3), match='cow'>
Criando diretórios e pastas de validação
[7]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
# Make the validation directories
try:
    path = base_dir + "/val/lion"
    os.makedirs(path, exist_ok=True)
    path = base_dir + "/val/tiger"
    os.makedirs(path, exist_ok=True)
    path = base_dir + "/val/cow"
    os.makedirs(path, exist_ok=True)
except OSError:
    print ("Creation of the directory failed")
else:
    print ("Successfully created the directory")
Successfully created the directory
[8]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
# Create validation folder

lion_train = base_dir + "/train/lion"
lion_val = base_dir + "/val/lion/"
tiger_train = base_dir + "/train/tiger/"
tiger_val = base_dir + "/val/tiger/"
cow_train = base_dir + "/train/cow/"
cow_val = base_dir + "/val/cow/"
lion_files = os.listdir(lion_train)
tiger_files = os.listdir(tiger_train)
cow_files = os.listdir(cow_train)
[10]
0s
  1
print(lion_files)
['lion_257.jpg', 'lion_37.jpg', 'lion_455.jpg', 'lion_239.jpg', 'lion_10.jpg', 'lion_271.jpg', 'lion_147.jpg', 'lion_61.jpg', 'lion_276.jpg', 'lion_36.jpg', 'lion_243.jpg', 'lion_66.jpg', 'lion_225.jpg', 'lion_286.jpg', 'lion_162.jpg', 'lion_349.jpg', 'lion_12.jpg', 'lion_99.jpg', 'lion_71.jpg', 'lion_339.jpg', 'lion_329.jpg', 'lion_459.jpg', 'lion_410.jpg', 'lion_298.jpg', 'lion_181.jpg', 'lion_312.jpg', 'lion_92.jpg', 'lion_207.jpg', 'lion_39.jpg', 'lion_127.jpg', 'lion_413.jpg', 'lion_230.jpg', 'lion_112.jpg', 'lion_83.jpg', 'lion_371.jpg', 'lion_321.jpg', 'lion_354.jpg', 'lion_191.jpg', 'lion_255.jpg', 'lion_60.jpg', 'lion_274.jpg', 'lion_391.jpg', 'lion_90.jpg', 'lion_429.jpg', 'lion_268.jpg', 'lion_164.jpg', 'lion_362.jpg', 'lion_379.jpg', 'lion_17.jpg', 'lion_220.jpg', 'lion_355.jpg', 'lion_222.jpg', 'lion_205.jpg', 'lion_105.jpg', 'lion_82.jpg', 'lion_101.jpg', 'lion_287.jpg', 'lion_364.jpg', 'lion_219.jpg', 'lion_381.jpg', 'lion_411.jpg', 'lion_131.jpg', 'lion_166.jpg', 'lion_284.jpg', 'lion_285.jpg', 'lion_217.jpg', 'lion_129.jpg', 'lion_293.jpg', 'lion_224.jpg', 'lion_236.jpg', 'lion_152.jpg', 'lion_41.jpg', 'lion_302.jpg', 'lion_368.jpg', 'lion_51.jpg', 'lion_43.jpg', 'lion_353.jpg', 'lion_55.jpg', 'lion_132.jpg', 'lion_44.jpg', 'lion_425.jpg', 'lion_176.jpg', 'lion_350.jpg', 'lion_246.jpg', 'lion_175.jpg', 'lion_42.jpg', 'lion_218.jpg', 'lion_153.jpg', 'lion_407.jpg', 'lion_348.jpg', 'lion_68.jpg', 'lion_326.jpg', 'lion_171.jpg', 'lion_9.jpg', 'lion_428.jpg', 'lion_100.jpg', 'lion_344.jpg', 'lion_404.jpg', 'lion_201.jpg', 'lion_126.jpg', 'lion_318.jpg', 'lion_385.jpg', 'lion_357.jpg', 'lion_87.jpg', 'lion_461.jpg', 'lion_57.jpg', 'lion_149.jpg', 'lion_408.jpg', 'lion_137.jpg', 'lion_103.jpg', 'lion_53.jpg', 'lion_259.jpg', 'lion_79.jpg', 'lion_278.jpg', 'lion_377.jpg', 'lion_144.jpg', 'lion_161.jpg', 'lion_358.jpg', 'lion_267.jpg', 'lion_108.jpg', 'lion_442.jpg', 'lion_226.jpg', 'lion_288.jpg', 'lion_85.jpg', 'lion_199.jpg', 'lion_134.jpg', 'lion_84.jpg', 'lion_396.jpg', 'lion_125.jpg', 'lion_23.jpg', 'lion_110.jpg', 'lion_453.jpg', 'lion_209.jpg', 'lion_366.jpg', 'lion_124.jpg', 'lion_440.jpg', 'lion_155.jpg', 'lion_322.jpg', 'lion_352.jpg', 'lion_107.jpg', 'lion_296.jpg', 'lion_19.jpg', 'lion_106.jpg', 'lion_264.jpg', 'lion_172.jpg', 'lion_62.jpg', 'lion_454.jpg', 'lion_443.jpg', 'lion_203.jpg', 'lion_154.jpg', 'lion_143.jpg', 'lion_128.jpg', 'lion_245.jpg', 'lion_361.jpg', 'lion_451.jpg', 'lion_182.jpg', 'lion_231.jpg', 'lion_98.jpg', 'lion_16.jpg', 'lion_77.jpg', 'lion_133.jpg', 'lion_380.jpg', 'lion_148.jpg', 'lion_295.jpg', 'lion_174.jpg', 'lion_67.jpg', 'lion_228.jpg', 'lion_254.jpg', 'lion_111.jpg', 'lion_261.jpg', 'lion_135.jpg', 'lion_168.jpg', 'lion_14.jpg', 'lion_297.jpg', 'lion_313.jpg', 'lion_356.jpg', 'lion_242.jpg', 'lion_146.jpg', 'lion_102.jpg', 'lion_422.jpg', 'lion_420.jpg', 'lion_327.jpg', 'lion_369.jpg', 'lion_310.jpg', 'lion_346.jpg', 'lion_395.jpg', 'lion_193.jpg', 'lion_338.jpg', 'lion_54.jpg', 'lion_32.jpg', 'lion_86.jpg', 'lion_159.jpg', 'lion_240.jpg', 'lion_291.jpg', 'lion_194.jpg', 'lion_169.jpg', 'lion_117.jpg', 'lion_158.jpg', 'lion_417.jpg', 'lion_272.jpg', 'lion_347.jpg', 'lion_258.jpg', 'lion_330.jpg', 'lion_382.jpg', 'lion_393.jpg', 'lion_270.jpg', 'lion_76.jpg', 'lion_13.jpg', 'lion_141.jpg', 'lion_340.jpg', 'lion_177.jpg', 'lion_234.jpg', 'lion_332.jpg', 'lion_388.jpg', 'lion_292.jpg', 'lion_73.jpg', 'lion_319.jpg', 'lion_446.jpg', 'lion_317.jpg', 'lion_456.jpg', 'lion_445.jpg', 'lion_65.jpg', 'lion_253.jpg', 'lion_237.jpg', 'lion_74.jpg', 'lion_433.jpg', 'lion_48.jpg', 'lion_247.jpg', 'lion_403.jpg', 'lion_150.jpg', 'lion_200.jpg', 'lion_221.jpg', 'lion_431.jpg', 'lion_178.jpg', 'lion_448.jpg', 'lion_324.jpg', 'lion_303.jpg', 'lion_387.jpg', 'lion_81.jpg', 'lion_471.jpg', 'lion_196.jpg', 'lion_250.jpg', 'lion_35.jpg', 'lion_438.jpg', 'lion_252.jpg', 'lion_47.jpg', 'lion_248.jpg', 'lion_316.jpg', 'lion_434.jpg', 'lion_140.jpg', 'lion_449.jpg', 'lion_323.jpg', 'lion_273.jpg', 'lion_56.jpg', 'lion_363.jpg', 'lion_426.jpg', 'lion_227.jpg', 'lion_192.jpg', 'lion_116.jpg', 'lion_458.jpg', 'lion_33.jpg', 'lion_416.jpg', 'lion_8.jpg', 'lion_262.jpg', 'lion_75.jpg', 'lion_406.jpg', 'lion_447.jpg', 'lion_345.jpg', 'lion_265.jpg', 'lion_7.jpg', 'lion_335.jpg', 'lion_59.jpg', 'lion_419.jpg', 'lion_198.jpg', 'lion_202.jpg', 'lion_64.jpg', 'lion_378.jpg', 'lion_389.jpg', 'lion_5.jpg', 'lion_462.jpg', 'lion_157.jpg', 'lion_289.jpg', 'lion_256.jpg', 'lion_437.jpg', 'lion_336.jpg', 'lion_78.jpg', 'lion_334.jpg', 'lion_470.jpg', 'lion_365.jpg', 'lion_45.jpg', 'lion_18.jpg', 'lion_412.jpg', 'lion_405.jpg', 'lion_6.jpg', 'lion_333.jpg', 'lion_210.jpg', 'lion_444.jpg', 'lion_109.jpg', 'lion_223.jpg', 'lion_136.jpg', 'lion_390.jpg', 'lion_130.jpg', 'lion_170.jpg', 'lion_457.jpg', 'lion_351.jpg', 'lion_72.jpg', 'lion_263.jpg', 'lion_15.jpg', 'lion_34.jpg', 'lion_300.jpg', 'lion_427.jpg', 'lion_436.jpg', 'lion_24.jpg', 'lion_165.jpg', 'lion_163.jpg', 'lion_260.jpg', 'lion_314.jpg', 'lion_441.jpg', 'lion_195.jpg', 'lion_460.jpg', 'lion_40.jpg', 'lion_311.jpg', 'lion_423.jpg', 'lion_241.jpg', 'lion_439.jpg', 'lion_386.jpg', 'lion_69.jpg', 'lion_180.jpg', 'lion_183.jpg', 'lion_233.jpg', 'lion_343.jpg', 'lion_367.jpg', 'lion_38.jpg']
Retirando imagens das pastas de treino e inserindo nas suas respectivas pastas de validação
[11]
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
# This will put images from the two training folders
# into their respective validation folders

for f in lion_files:
    validationCatsSearchObj = re.search("\d\d\d", f)
    if validationCatsSearchObj:
        shutil.move(f'{lion_train}/{f}', lion_val)

for f in tiger_files:
    validationCatsSearchObj = re.search("\d\d\d", f)
    if validationCatsSearchObj:
        shutil.move(f'{tiger_train}/{f}', tiger_val)

for f in cow_files:
    validationCatsSearchObj = re.search("\d\d\d", f)
    if validationCatsSearchObj:
        shutil.move(f'{cow_train}/{f}', cow_val)
[12]
0s
  1
!ls PetImages/val/lion/
lion_100.jpg  lion_171.jpg  lion_248.jpg  lion_324.jpg	lion_395.jpg
lion_101.jpg  lion_172.jpg  lion_250.jpg  lion_326.jpg	lion_396.jpg
lion_102.jpg  lion_174.jpg  lion_252.jpg  lion_327.jpg	lion_403.jpg
lion_103.jpg  lion_175.jpg  lion_253.jpg  lion_329.jpg	lion_404.jpg
lion_105.jpg  lion_176.jpg  lion_254.jpg  lion_330.jpg	lion_405.jpg
lion_106.jpg  lion_177.jpg  lion_255.jpg  lion_332.jpg	lion_406.jpg
lion_107.jpg  lion_178.jpg  lion_256.jpg  lion_333.jpg	lion_407.jpg
lion_108.jpg  lion_180.jpg  lion_257.jpg  lion_334.jpg	lion_408.jpg
lion_109.jpg  lion_181.jpg  lion_258.jpg  lion_335.jpg	lion_410.jpg
lion_110.jpg  lion_182.jpg  lion_259.jpg  lion_336.jpg	lion_411.jpg
lion_111.jpg  lion_183.jpg  lion_260.jpg  lion_338.jpg	lion_412.jpg
lion_112.jpg  lion_191.jpg  lion_261.jpg  lion_339.jpg	lion_413.jpg
lion_116.jpg  lion_192.jpg  lion_262.jpg  lion_340.jpg	lion_416.jpg
lion_117.jpg  lion_193.jpg  lion_263.jpg  lion_343.jpg	lion_417.jpg
lion_124.jpg  lion_194.jpg  lion_264.jpg  lion_344.jpg	lion_419.jpg
lion_125.jpg  lion_195.jpg  lion_265.jpg  lion_345.jpg	lion_420.jpg
lion_126.jpg  lion_196.jpg  lion_267.jpg  lion_346.jpg	lion_422.jpg
lion_127.jpg  lion_198.jpg  lion_268.jpg  lion_347.jpg	lion_423.jpg
lion_128.jpg  lion_199.jpg  lion_270.jpg  lion_348.jpg	lion_425.jpg
lion_129.jpg  lion_200.jpg  lion_271.jpg  lion_349.jpg	lion_426.jpg
lion_130.jpg  lion_201.jpg  lion_272.jpg  lion_350.jpg	lion_427.jpg
lion_131.jpg  lion_202.jpg  lion_273.jpg  lion_351.jpg	lion_428.jpg
lion_132.jpg  lion_203.jpg  lion_274.jpg  lion_352.jpg	lion_429.jpg
lion_133.jpg  lion_205.jpg  lion_276.jpg  lion_353.jpg	lion_431.jpg
lion_134.jpg  lion_207.jpg  lion_278.jpg  lion_354.jpg	lion_433.jpg
lion_135.jpg  lion_209.jpg  lion_284.jpg  lion_355.jpg	lion_434.jpg
lion_136.jpg  lion_210.jpg  lion_285.jpg  lion_356.jpg	lion_436.jpg
lion_137.jpg  lion_217.jpg  lion_286.jpg  lion_357.jpg	lion_437.jpg
lion_140.jpg  lion_218.jpg  lion_287.jpg  lion_358.jpg	lion_438.jpg
lion_141.jpg  lion_219.jpg  lion_288.jpg  lion_361.jpg	lion_439.jpg
lion_143.jpg  lion_220.jpg  lion_289.jpg  lion_362.jpg	lion_440.jpg
lion_144.jpg  lion_221.jpg  lion_291.jpg  lion_363.jpg	lion_441.jpg
lion_146.jpg  lion_222.jpg  lion_292.jpg  lion_364.jpg	lion_442.jpg
lion_147.jpg  lion_223.jpg  lion_293.jpg  lion_365.jpg	lion_443.jpg
lion_148.jpg  lion_224.jpg  lion_295.jpg  lion_366.jpg	lion_444.jpg
lion_149.jpg  lion_225.jpg  lion_296.jpg  lion_367.jpg	lion_445.jpg
lion_150.jpg  lion_226.jpg  lion_297.jpg  lion_368.jpg	lion_446.jpg
lion_152.jpg  lion_227.jpg  lion_298.jpg  lion_369.jpg	lion_447.jpg
lion_153.jpg  lion_228.jpg  lion_300.jpg  lion_371.jpg	lion_448.jpg
lion_154.jpg  lion_230.jpg  lion_302.jpg  lion_377.jpg	lion_449.jpg
lion_155.jpg  lion_231.jpg  lion_303.jpg  lion_378.jpg	lion_451.jpg
lion_157.jpg  lion_233.jpg  lion_310.jpg  lion_379.jpg	lion_453.jpg
lion_158.jpg  lion_234.jpg  lion_311.jpg  lion_380.jpg	lion_454.jpg
lion_159.jpg  lion_236.jpg  lion_312.jpg  lion_381.jpg	lion_455.jpg
lion_161.jpg  lion_237.jpg  lion_313.jpg  lion_382.jpg	lion_456.jpg
lion_162.jpg  lion_239.jpg  lion_314.jpg  lion_385.jpg	lion_457.jpg
lion_163.jpg  lion_240.jpg  lion_316.jpg  lion_386.jpg	lion_458.jpg
lion_164.jpg  lion_241.jpg  lion_317.jpg  lion_387.jpg	lion_459.jpg
lion_165.jpg  lion_242.jpg  lion_318.jpg  lion_388.jpg	lion_460.jpg
lion_166.jpg  lion_243.jpg  lion_319.jpg  lion_389.jpg	lion_461.jpg
lion_168.jpg  lion_245.jpg  lion_321.jpg  lion_390.jpg	lion_462.jpg
lion_169.jpg  lion_246.jpg  lion_322.jpg  lion_391.jpg	lion_470.jpg
lion_170.jpg  lion_247.jpg  lion_323.jpg  lion_393.jpg	lion_471.jpg
Importando bibliotecas
[13]
6s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
from __future__ import print_function, division

import torch
import torch.nn as nn
import torch.optim as optim
from torch.optim import lr_scheduler
import torchvision
from torchvision import datasets, models, transforms
import matplotlib.pyplot as plt
import numpy as np
import time
import os
import copy
Definindo transformações para aumentar a variabilidade das imagens, através de re-cálcuco de tamanhos, recortes de pedaços, rotações, normalização e transformações em Tensor.
[14]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
# Make transforms and use data loaders

# We'll use these a lot, so make them variables
mean_nums = [0.485, 0.456, 0.406]
std_nums = [0.229, 0.224, 0.225]

chosen_transforms = {'train': transforms.Compose([
        transforms.RandomResizedCrop(size=256),
        transforms.RandomRotation(degrees=15),
        transforms.RandomHorizontalFlip(),
        transforms.ToTensor(),
        transforms.Normalize(mean_nums, std_nums)
]), 'val': transforms.Compose([
        transforms.Resize(256),
        transforms.CenterCrop(224),
        transforms.ToTensor(),
        transforms.Normalize(mean_nums, std_nums)
]),
}
Construção do dataset
[15]
0s
  1
  2
  3
  4
  5
# Set the directory for the data
data_dir = 'PetImages/'

# Use the image folder function to create datasets
chosen_datasets = {x: datasets.ImageFolder(os.path.join(data_dir, x), chosen_transforms[x]) for x in ['train', 'val']}
Criando dataloaders para obter imagens iteráveis
[16]
0s
  1
  2
  3
  4
# Make iterables with the dataloaders
dataloaders = {x: torch.utils.data.DataLoader(chosen_datasets[x], batch_size=4,
  shuffle=True, num_workers=4)
              for x in ['train', 'val']}
/usr/local/lib/python3.7/dist-packages/torch/utils/data/dataloader.py:481: UserWarning: This DataLoader will create 4 worker processes in total. Our suggested max number of worker in current system is 2, which is smaller than what this DataLoader is going to create. Please be aware that excessive worker creation might get DataLoader running slow or even freeze, lower the worker number to avoid potential slowness/freeze if necessary.
  cpuset_checked))
[17]
0s
  1
dataloaders
{'train': <torch.utils.data.dataloader.DataLoader at 0x7fd70715d810>,
 'val': <torch.utils.data.dataloader.DataLoader at 0x7fd606e8dd90>}
Vamos precisar preservar algumas informações sobre nosso conjunto de dados, especificando o tamanho do conjunto de dados, nomes das classes e especificando o tipo de dispositivo ( GPU ).
[18]
0s
  1
  2
  3
  4
dataset_sizes = {x: len(chosen_datasets[x]) for x in ['train', 'val']}
class_names = chosen_datasets['train'].classes

device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
Visualização de Datasets e Classes
[19]
0s
  1
  2
print(dataset_sizes)
print(class_names)
{'train': 222, 'val': 776}
['cow', 'lion', 'tiger']
Visualização de imagens com uma função. Pegando uma entrada, criando uma matriz Numpy a partir dela e a transpondo a mesma. Em seguida, normaliza-se a entrada usando média e desvio padrão. Por fim, recorta-se os valores entre 0 e 1 para que não haja um intervalo enorme nos valores possíveis do array e, em seguida, mostraremos a imagem:
[20]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
# Visualize some images
def imshow(inp, title=None):
    inp = inp.numpy().transpose((1, 2, 0))
    mean = np.array([mean_nums])
    std = np.array([std_nums])
    inp = std * inp + mean
    inp = np.clip(inp, 0, 1)
    plt.imshow(inp)
    if title is not None:
        plt.title(title)
    plt.pause(0.001)  # Pause a bit so that plots are updated
Visualizando alguns dos dados
[21]
2s
  1
  2
  3
  4
  5
  6
  7
# Grab some of the training data to visualize
inputs, classes = next(iter(dataloaders['train']))

# Now we construct a grid from batch
out = torchvision.utils.make_grid(inputs)

imshow(out, title=[class_names[x] for x in classes])

Realizando set do modelo e o download da resnet34 (Pré-treinada) para utilização dos pesos para treinamento
[22]
0s
  1
  2
  3
  4
  5
  6
  7
# Setting up the model
# load in pretrained and reset final fully connected

res_mod = models.resnet34(pretrained=True)

num_ftrs = res_mod.fc.in_features
res_mod.fc = nn.Linear(num_ftrs, 3)

Visualização da composição do modelo
[23]
0s
  1
  2
for name, child in res_mod.named_children():
    print(name)
conv1
bn1
relu
maxpool
layer1
layer2
layer3
layer4
avgpool
fc
A parte final "fc" (Fully-Connected) é a camada que estamos modificando a forma, dando-a três classes de saída.
Essencialmente, vamos alterar as saídas da parte final totalmente conectada para apenas duas classes e ajustar os pesos para todas as outras camadas.

Agora precisamos enviar nosso modelo para nosso dispositivo de treinamento. Também precisamos escolher o critério de perda e o otimizador que queremos usar com o modelo. CrossEntropyLoss e o otimizador SGD são boas escolhas, embora existam muitos outros.

Também escolheremos um agendador de taxa de aprendizado, que diminui a taxa de aprendizado do otimizador de horas extras e ajuda a evitar a não convergência devido a grandes taxas de aprendizado. Você pode aprender mais sobre programadores de taxa de aprendizado aqui se estiver curioso:

[24]
0s
  1
  2
  3
  4
  5
  6
  7
  8
res_mod = res_mod.to(device)
criterion = nn.CrossEntropyLoss()

# Observe that all parameters are being optimized
optimizer_ft = optim.SGD(res_mod.parameters(), lr=0.001, momentum=0.9)

# Decay LR by a factor of 0.1 every 7 epochs
exp_lr_scheduler = lr_scheduler.StepLR(optimizer_ft, step_size=7, gamma=0.1)
Definindo as funções que irão treinar o modelo e visualizar as previsões.Vamos começar com a função de treinamento. Levará em nosso modelo escolhido, bem como o otimizador, critério e escalonador que escolhemos. Também especificaremos um número padrão de épocas de treinamento.
Cada época terá uma fase de treinamento e validação. Para começar, definimos os melhores pesos iniciais do modelo para aqueles do modo pré-treinado, usando state_dict.
Agora, para cada época no número escolhido de épocas, se estivermos na fase de treinamento, iremos:
*Diminua a taxa de aprendizado
*Zere os gradientes
*Executar o passe de treinamento para a frente
*Calcule a perda
*Faça a "back-propagation" e atualize os pesos com o otimizador
[25]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
def train_model(model, criterion, optimizer, scheduler, num_epochs=10):
    since = time.time()

    best_model_wts = copy.deepcopy(model.state_dict())
    best_acc = 0.0

    for epoch in range(num_epochs):
        print('Epoch {}/{}'.format(epoch, num_epochs - 1))
        print('-' * 10)

        # Each epoch has a training and validation phase
        for phase in ['train', 'val']:
            if phase == 'train':
                scheduler.step()
                model.train()  # Set model to training mode
            else:
                model.eval()   # Set model to evaluate mode

            current_loss = 0.0
            current_corrects = 0

            # Here's where the training happens
            print('Iterating through data...')

            for inputs, labels in dataloaders[phase]:
                inputs = inputs.to(device)
                labels = labels.to(device)

                # We need to zero the gradients, don't forget it
                optimizer.zero_grad()

                # Time to carry out the forward training poss
                # We only need to log the loss stats if we are in training phase
                with torch.set_grad_enabled(phase == 'train'):
                    outputs = model(inputs)
                    _, preds = torch.max(outputs, 1)
                    loss = criterion(outputs, labels)

                    # backward + optimize only if in training phase
                    if phase == 'train':
                        loss.backward()
                        optimizer.step()

                # We want variables to hold the loss statistics
                current_loss += loss.item() * inputs.size(0)
                current_corrects += torch.sum(preds == labels.data)

            epoch_loss = current_loss / dataset_sizes[phase]
            epoch_acc = current_corrects.double() / dataset_sizes[phase]

            print('{} Loss: {:.4f} Acc: {:.4f}'.format(
                phase, epoch_loss, epoch_acc))

            # Make a copy of the model if the accuracy on the validation set has improved
            if phase == 'val' and epoch_acc > best_acc:
                best_acc = epoch_acc
                best_model_wts = copy.deepcopy(model.state_dict())

        print()

    time_since = time.time() - since
    print('Training complete in {:.0f}m {:.0f}s'.format(
        time_since // 60, time_since % 60))
    print('Best val Acc: {:4f}'.format(best_acc))

    # Now we'll load in the best model weights and return it
    model.load_state_dict(best_model_wts)
    return model
Função para visualização das predições realizadas pelo modelo
[26]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
def visualize_model(model, num_images=12):
    was_training = model.training
    model.eval()
    images_handeled = 0
    fig = plt.figure()

    with torch.no_grad():
        for i, (inputs, labels) in enumerate(dataloaders['val']):
            inputs = inputs.to(device)
            labels = labels.to(device)

            outputs = model(inputs)
            _, preds = torch.max(outputs, 1)

            for j in range(inputs.size()[0]):
                images_handeled += 1
                ax = plt.subplot(num_images//2, 2, images_handeled)
                ax.axis('off')
                ax.set_title('predicted: {}'.format(class_names[preds[j]]))
                imshow(inputs.cpu().data[j])

                if images_handeled == num_images:
                    model.train(mode=was_training)
                    return
        model.train(mode=was_training)
Treinando o modelo com as imagens e mostrando previsões
[27]
13min
  1
  2
  3
base_model = train_model(res_mod, criterion, optimizer_ft, exp_lr_scheduler, num_epochs=3)
visualize_model(base_model)
plt.show()

[28]
0s
  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
# Setting up the model
# Note that the parameters of imported models are set to requires_grad=True by default

res_mod = models.resnet34(pretrained=True)
for param in res_mod.parameters():
    param.requires_grad = False

num_ftrs = res_mod.fc.in_features
res_mod.fc = nn.Linear(num_ftrs, 3)

res_mod = res_mod.to(device)
criterion = nn.CrossEntropyLoss()

# Here's another change: instead of all parameters being optimized
# only the params of the final layers are being optimized

optimizer_ft = optim.SGD(res_mod.fc.parameters(), lr=0.001, momentum=0.9)

exp_lr_scheduler = lr_scheduler.StepLR(optimizer_ft, step_size=7, gamma=0.1)
[29]
0s
  1
  2
for name, child in res_mod.named_children():
    print(name)
conv1
bn1
relu
maxpool
layer1
layer2
layer3
layer4
avgpool
fc
[30]
0s
  1
  2
  3
  4
  5
  6
  7
  8
for name, child in res_mod.named_children():
    if name in ['layer3', 'layer4']:
        print(name + 'has been unfrozen.')
        for param in child.parameters():
            param.requires_grad = True
    else:
        for param in child.parameters():
            param.requires_grad = False
layer3has been unfrozen.
layer4has been unfrozen.
[31]
0s
  1
optimizer_conv = torch.optim.SGD(filter(lambda x: x.requires_grad, res_mod.parameters()), lr=0.001, momentum=0.9)
[32]
12min
  1
  2
  3
base_model = train_model(res_mod, criterion, optimizer_conv, exp_lr_scheduler, num_epochs=3)
visualize_model(base_model)
plt.show()

[33]
0s
  1
  2
!mkdir models/

[34]
0s
  1
torch.save(base_model.state_dict(), "/content/models/test.pt" )
[35]
0s
  1
  2
base_model.load_state_dict(torch.load("/content/models/test.pt"))
base_model.eval()
ResNet(
  (conv1): Conv2d(3, 64, kernel_size=(7, 7), stride=(2, 2), padding=(3, 3), bias=False)
  (bn1): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
  (relu): ReLU(inplace=True)
  (maxpool): MaxPool2d(kernel_size=3, stride=2, padding=1, dilation=1, ceil_mode=False)
  (layer1): Sequential(
    (0): BasicBlock(
      (conv1): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (1): BasicBlock(
      (conv1): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (2): BasicBlock(
      (conv1): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
  )
  (layer2): Sequential(
    (0): BasicBlock(
      (conv1): Conv2d(64, 128, kernel_size=(3, 3), stride=(2, 2), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (downsample): Sequential(
        (0): Conv2d(64, 128, kernel_size=(1, 1), stride=(2, 2), bias=False)
        (1): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      )
    )
    (1): BasicBlock(
      (conv1): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (2): BasicBlock(
      (conv1): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (3): BasicBlock(
      (conv1): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
  )
  (layer3): Sequential(
    (0): BasicBlock(
      (conv1): Conv2d(128, 256, kernel_size=(3, 3), stride=(2, 2), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (downsample): Sequential(
        (0): Conv2d(128, 256, kernel_size=(1, 1), stride=(2, 2), bias=False)
        (1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      )
    )
    (1): BasicBlock(
      (conv1): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (2): BasicBlock(
      (conv1): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (3): BasicBlock(
      (conv1): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (4): BasicBlock(
      (conv1): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (5): BasicBlock(
      (conv1): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
  )
  (layer4): Sequential(
    (0): BasicBlock(
      (conv1): Conv2d(256, 512, kernel_size=(3, 3), stride=(2, 2), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (downsample): Sequential(
        (0): Conv2d(256, 512, kernel_size=(1, 1), stride=(2, 2), bias=False)
        (1): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      )
    )
    (1): BasicBlock(
      (conv1): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
    (2): BasicBlock(
      (conv1): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn1): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
      (relu): ReLU(inplace=True)
      (conv2): Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
      (bn2): BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
    )
  )
  (avgpool): AdaptiveAvgPool2d(output_size=(1, 1))
  (fc): Linear(in_features=512, out_features=3, bias=True)
)
Conclusão
Foi implementado um modelo de redes neurais com um dataset de três classes, contendo 999 imagens. O treinamento foi realizado em 12m 9s com os seguintes resultados:

val Loss: 0.0429
Best val Acc: 0.996134
