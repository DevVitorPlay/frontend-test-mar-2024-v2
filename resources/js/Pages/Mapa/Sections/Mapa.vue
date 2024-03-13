<script setup>
    import { ref, onMounted } from 'vue';
    import { Link } from '@inertiajs/vue3';

    import 'leaflet';
    import 'leaflet/dist/leaflet.css';
    import 'proj4';
    import 'proj4leaflet';
    import 'leaflet-mouse-position';
    import 'leaflet.vectorgrid';

    import {
        ConfigsLeaflet,
        AdicionaCoordenadasMouse,
        AdicionaEscala,
        FuncaoVisaoInicial,
        AdicionaAttribution,
        CriaMenuContexto,
        FuncaoMapaInformacoes,
        FuncoesZoom
    } from '@/Pages/Mapa/Functions/InicializarMapa.js';

    import { AdicionaBasemapPadrao } from '@/Pages/Mapa/Functions/TileLayers/AdicionaBasemapPadrao.js';
    import { AdicionaOverlaysPadrao } from '@/Pages/Mapa/Functions/TileLayers/AdicionaOverlaysPadrao.js';
    import { ToggleRasterTile } from '@/Pages/Mapa/Functions/TileLayers/ToggleRasterTile.js';

    const props = defineProps({
        projeto: Object,
        rasters: Object
    });

    let configsMapa = props.projeto.mapa.configuracao;

    let rasters = props.projeto.rasters;

    let map = ref(null);
    const zoomIn = () => {
        if (map) {
            map.zoomIn();
        }
    };
    const zoomOut = () => {
        if (map) {
            map.zoomOut();
        }
    };


    onMounted(() => {
        // Objeto com as configurações do Leaflet para criação do objeto map
        let configs = ConfigsLeaflet(configsMapa);

        // Cria o objeto map do Leaflet
        map = L.map('map', configs);

        // Adiciona a função "SetaVisaoInicial" de resetar a visão inicial do mapa
        FuncaoVisaoInicial(map, configsMapa.visaoInicial.x, configsMapa.visaoInicial.y, configsMapa.visaoInicial.z);

        // Seta a visualização inicial do mapa
        SetaVisaoInicial();

        // Adiciona as funções de zoom do mapa
        FuncoesZoom(map);
        // Adiciona a função "MapaInformacoes" para mostrar as informações do mapa
        FuncaoMapaInformacoes(map);

        // Adiciona as coordenadas do mouse no canto inferior direito do mapa
        configsMapa.funcionalidades.coordenadasMouse ? AdicionaCoordenadasMouse(map, configsMapa.configuracoesLeaflet) : configsMapa.funcionalidades.coordenadasMouse;

        // Desabilitar o clique-duplo para função de zoom (nativa do Leaflet)
        map.doubleClickZoom.disable();

        // Adiciona escala ao mapa caso configsMapa.funcionalidades.escala seja true
        configsMapa.funcionalidades.escala ? AdicionaEscala(map) : configsMapa.funcionalidades.escala;

        // Adiciona atribuições (fonte de dados) ao mapa    
        configsMapa.funcionalidades.atribuicoes ? AdicionaAttribution(map, configsMapa.configuracoesLeaflet.atribuicaoPrefixo) : map.attributionControl.remove();

        // Desativa o clique do botão direito para evitar menu de contexto do navegador e cria o menu de contexto (clique direito com coordenadas)
        configsMapa.funcionalidades.menuContexto ? CriaMenuContexto(map, configsMapa.configuracoesLeaflet) : configsMapa.funcionalidades.menuContexto;

        // Adiciona o basemap padrão do mapa (TileLayers)
        AdicionaBasemapPadrao(map, rasters);

        // Adiciona os overlays (TileLayers)
        AdicionaOverlaysPadrao(map, rasters);

        // Cria a função "ToggleRaster" para alternar a visualização dos overlays
        window.ToggleRaster = function (nomeRaster) {
            rasters.forEach(raster => raster.nome == nomeRaster ? ToggleRasterTile(map, raster) : null);
        };

    });
</script>

<template>
    <div class="min-h-screen bg-dots-darker bg-center bg-gray-100 dark:bg-dots-lighter dark:bg-gray-900 selection:bg-red-500 selection:text-white">
      <div class="sm:flex w-full h-20 sm:items-center sm:flex-row p-4 justify-between">
        <div>
          <Link class="link" href="/">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              class="self-center shrink-0 stroke-red-500 w-6 h-6 mx-6" transform="rotate(180)">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M4.5 12h15m0 0l-6.75-6.75M19.5 12l-6.75 6.75" />
            </svg>
            <h2 class="text-xl font-bold text-white">Voltar para Home</h2>
          </Link>
        </div>
        <div>
          <Link class="link" href="/grafico">
            <h2 class="text-xl font-bold text-white">Ir para gráfico</h2>
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              class="self-center shrink-0 stroke-red-500 w-6 h-6 mx-6">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M4.5 12h15m0 0l-6.75-6.75M19.5 12l-6.75 6.75" />
            </svg>
          </Link>
        </div>
      </div>
      <div class="button-map">
        <button @click="zoomIn"
          class="bg-gray-200 hover:bg-gray-300 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center">
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 24 24"
            width="24" height="24">
            <path d="M0 0h24v24H0V0z" fill="none" />
            <path fill="currentColor"
              d="M12 3c.55 0 1 .45 1 1v7h7c.55 0 1 .45 1 1s-.45 1-1 1h-7v7c0 .55-.45 1-1 1s-1-.45-1-1v-7H4c-.55 0-1-.45-1-1s.45-1 1-1h7V4c0-.55.45-1 1-1z" />
          </svg>
        </button>
        <button @click="zoomOut"
          class="bg-gray-200 hover:bg-gray-300 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center mt-2">
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 24 24"
            width="24" height="24">
            <path d="M0 0h24v24H0V0z" fill="none" />
            <path fill="currentColor" d="M19 13H5c-.55 0-1-.45-1-1s.45-1 1-1h14c.55 0 1 .45 1 1s-.45 1-1 1z" />
          </svg>
        </button>
      </div>
      <div id="map" class="z-[5] h-[calc(80vh)] max-h-[calc(80vh)]"></div>
    </div>
  </template>