---
layout: page
title: "Podcasts de Linux"
desc: "Lista de post ordenados por etiquetas"
permalink: /podcasts/

sitemap:
  priority: .5
---
[Desarrollado por atareao.es](https://www.atareao.es/)

Abre con VLC
<a href="https://ugeek.github.io/podcasts.m3u"><img style="float: left;" src="/img/icon/play.png" alt="" width="30" height="30" /></a>

<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>HTML5 Audio Player</title>
    <script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/3.2.1/jquery.min.js"></script>

    <script type="text/javascript" >
    var audio;
    var playlist;
    var tracks;
    var current;
    var previous;
    var current_track;
    var previous_track;
    var ntracks;
    function initaudio(){
        audio=$("audio");
        playlist=$("#playlist");
        ntracks=$("[id^=item-]").length
        audio[0].volume=1;
        current=0;
        previous=ntracks-1;
        current_track=playlist.find("#item-0");
        previous_track=playlist.find("#item-"+previous);
        runaudio(current_track, audio[0],false);
        $("[id^=item-]").click(function(e){
            e.preventDefault();
            previous=current;
            previous_track=current_track;
            remove_play(previous_track);
            current_track=$(this);
            current=current_track.parent().index();
            runaudio(current_track, audio[0]);
        });
        audio[0].addEventListener("ended",function(e){
            playnext();
        });
        audio[0].addEventListener("pause",function(e){
            $("#playing").hide();
        });
        audio[0].addEventListener("play",function(e){
            $("#playing").show();
        });
    };
    function playnext(){
        previous=current;
        previous_track=current_track;
        remove_play(previous_track);
        current++;
        current_track=playlist.find("#item-"+current);
        if(current_track.length==0){
            current=0;
            current_track=playlist.find("#item-0");
        }
        runaudio($(current_track),audio[0]);
    }
    function playprevious(){
        previous=current;
        previous_track=current_track;
        remove_play(previous_track);
        current--;
        current_track=playlist.find("#item-"+current);
        if(current<0){
            current=ntracks-1;
        }
        current_track=playlist.find("#item-"+current);
        runaudio($(current_track),audio[0]);
    }
    function remove_play(item){
        isp=$(item.find(".isplaying"));
        isp.html("");
    }
    function runaudio(item, player,play=true){
        isp=$(item.find(".isplaying"))
        isp.html("<i class='fa fa-play' aria-hidden='true'></i>");
        podcast=$(item.find(".podcast"));
        $("#podcast").text(podcast.text());
        track=$(item.find(".track"));
        if(track.text().length>33){
            $("#track").text(track.text().substring(0,30)+"...");
        }else{
            $("#track").text(track.text());
        }
        link=$(item.find('a'));
        player.src=link.attr("href");
        par=link.parent();
        par.addClass("active").siblings().removeClass("active");
        audio[0].load();
        if(play==true){
            console.log(play);
            audio[0].play();
        }
    }
    $(document).ready(function(){
        console.log($("[id^=item-]").length);
        $("#right").bind("click", function(e) {
            playnext();
        });
        $("#left").bind("click", function(e) {
            playprevious();
        });
        $("#playing").hide();
        initaudio();
    });
    </script>
    <link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css?family=Roboto" rel="stylesheet">
    <style>
        #left{
            margin-top: 7px;
            float: left;
            width: 16px;
            height: 32px;
            cursor:hand;
        }
        #right{
            margin-top: 7px;
            float:left;
            width: 16px;
            height: 32px;
            cursor:hand;
        }
        .compilandopodcast{
            background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAMAAABg3Am1AAAAYFBMVEUREyMZGywnGS1HGi1BIEEsLz9/HjfqHTe7LkQ0VktMTloAcBB9R1b6KUJHWXo1ckbFUV5pbHT4R1v2WGoAsw/Mb3robXyFipGghpqorbD2nqb2ur3Mz9Dz19jn6OX4+fWMNKc4AAAAAWJLR0QAiAUdSAAAAAlwSFlzAAAN1wAADdcBQiibeAAAAAd0SU1FB+EFBQoqJLANsOoAAAJcSURBVEjHzZQBd6MgDIBRCzKsrIBCISD//18uUNe6XbW3d+/dXVoxJHwkAYE0PxTyNwGqPm2ECpTnk20Bv77dkqtEcQAIHHfz+3V4RRTZAahoXC4ALcMXJygVviCePAWILwzqAsd7QVBTShFVeoerVOZ3N1Upx89N/CUG2VZMMIvPrIVSQjgaH5ZvAE5M1CaDYZr8uY0UK6LPAF8qwIRQdb5UL05SymEYBIbYqwErxvD0lrbygimPbfxaxVbHjDA6pl3qFs5RJSV1WNce4HIs6dKas2CMKeeQq9M8BXyOD3iYBvdGhZQYV7wGYm6u3RrjEKD3+odJOu/VdXg/Au5LTijOT+UV984fARuX9PFtmiTn8RCI9750lJ2u0pXP8QB4+IY354fpXX4xPgHuVZQv43RSLr8A8rJaMP/ovcwvgbzU89PIU4dZ5UPARZR6+BFhJ1qHo2nZA0gRVe+A6CuKO1lsxxcZdfdLYxG/dfMRPAtFnCD/+m79IdC2bWlv77XTbl0bgF1mzvh8YRfOL/xSlQtrOtT4auItn2e+Au2cbNKLAbMAJJN00tlm3ZwXgw6w2Sw29MmGwFYgwNjr3INdgk3oXXQ2Bcg2BfzhHD2YbCx8AjMY0FmDTVaXCLpHwBiz9BCSMWiyYYRHhIZpM3JtdK/xNWreMWyNGXVv9M1kRsaNHrs/3Ye269oGn64ratHa2mv3gC6BMQA6AZ8hjAGshaAB+D5gbdAW1xigH3XC4Sb0wbB9YBwtlO0wNmAgjAa4orbbBThuL6/Cyp9VjfHdGpp2fR7975b/8jx8AEVRQRkFDsQrAAAAAElFTkSuQmCC");
        }

        .eduardocollado{
            background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAMAAABg3Am1AAAAYFBMVEUAAwAHAQIICwYOEA0aHBknKCU0NjE+QjxGSkROUk1TVkhUWVNdYVtkaWNqcWFvdG5+hXyDhYGRk46OlYycoJqmqqSusqy3urXAw7/LzsvY2tfj5eLs7uvx8/D3+fb9//wadFjiAAAAAWJLR0QAiAUdSAAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB+EFBQoqBItjkCIAAABBdEVYdENvbW1lbnQAQ1JFQVRPUjogZ2QtanBlZyB2MS4wICh1c2luZyBJSkcgSlBFRyB2NjIpLCBxdWFsaXR5ID0gOTAKsEVYkwAABBVJREFUSMeVlut2tCoMhikKSIEiSDiKc/93uYNjO/awf3yZrjWti8ckbw6U9D0lLSbyhkbI+fVGZmVXCKW0/svI48h5NfQ6SS6MrauFENvjlw0gbIzQCX8oneZpmueJMruFNQKU4w8geUEJJdwapVwI4JyR7H210fsA+fgFdMCACOEhl1L3vR8PzMq9C66s5Nz+JEgvfsbzk8q1DUPk0VMBxdmMAc6m/AAaKDxPmMut4gcBJPacNztPb4TS2X3PnFQ/VKEyDKA9gX7UHL2kKBidRP4BsFN4B6XVp4O946dmZ2cUmUzMfwcivh8jClDqJ3BaiYaNWMlkv8VE5DwqJSDVE/giWgN+AkSUx00pwkbOVMd8AWcSA6jVnOcpC4/jRRC34ENMYXjAQ/vQ9TjQQS366YFDazegYRXoElIZ7y/IoEitJOyKLJ/Akku9ARkjpWp1kGupo9g1ei0WIX369BBqf8VE2siBcy6VtptNxVsl0PiivX3KJPJxz6EtE1uk8SGsBt8rFymVsR6C5+wJLN9lLXyWQhljFTpA6RfBjWZMe68o/5T1DiQsvrbCesH1YvxilHR+ZptdlFKjplSmfgcMpUuxQkhMQbk92GCtkdKGsLBpAKjSvt+S5tPEnUEnZgXtelHZ2wBW6FUYMYBJlwNV+kSImrGDYbNaa6Oh7cbtxXvA5E0aNcWi1n4H3IIT7DZErHEFa+dcAPDO+PqsHA5E30/iZMiOvcFrSjkla3EmsHC5Hz1BrcmNLmAKWr8AtLEECMsQ0YWyo6H6LlMtDmpJAbfJbEM+Z+oLeOycQYBgBZYPvB8RpZRKKTkKMk04vPU78Dgq7pNNC8akXjiHPUf0hESS1KSC6w6BfgMePfhtwzXBuJChYOOmfAKRUR3SObWnvQBwq9XYgXxxHmLELVMQyJYwreMLQDH6CRzFb7hMjXHpjAUSlJGDYM5Be51/LuNhDUNa0c6kvbcedcoZGBxH3/8Cdr+uuH09AAYUC66MjIVxvl874RfQQX9sIYRRPow+pxgDVvtri/wCHlUra9fN+YApp5BGHW2sv8/vF3DEZREas0Y3GFcK24fy+b6nPu0CHt2J93e9RVwDGH5cP951Suc++xvYo5XyY42n/CmBVsIPEDvrh5cB9ORwOle9bihSWMO2Gfw7xxRx8mJr171xAXtyEmeRBxjKWo0bQeE46xwhAx0XR213hghGzwslQlhXI9jMsKUWjTrlLM4BsmU/A3sauYxhD4VtxZaduVhsyr6Ua1VOXOhQW/0OUAUxQcAmXxZtU3TX+y+bTG054Z3ZXo8kYNibUUbjBe2yY+RuFO/ImeGWuD/CUfDWOY+ltqjDX8bs16/ndcZRH2O1mCn5H5tf55//ZeBFSy/+T5vIPxr9Z+A/SGudprzcys0AAAAASUVORK5CYII=");
        }
        .mosqueteroweb{
            background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAMAAABg3Am1AAAAYFBMVEUDBQEQEQ4hGRIaGxkqGQkyJRonKCY/Kxc0NjQ/NSxCQ0FfQiJZRzNRU1BgYmCDXTJ9alVucG2NfWeAgn+jhF6PkI2hj3zjjTWfoZ6tn47BrJaxs7DCw8DXwqTR1NH4+velZzBdAAAAAWJLR0QAiAUdSAAAAAlwSFlzAAAOxAAADsQBlSsOGwAAAAd0SU1FB+EFBQopGlpB/oIAAASVSURBVEjHXVXbYusoDBQWBoyBmFBSElP3//9yR9jp2VYPCQaNLiMhyDjnITHX1vZ97/3orabxWVJpreYk587n7J0zihgILIzzOBZA73uLsFAEUHPEGcSnnPDHRGaoi7hYTh97hkVXWo0pDX1mk0qJxvvhwUfvhg3oi4Nek0OITXA5ny48fOHLsyJlUkWcCFq0D0jPUC91B86liiQi4qtw4CJ8DQDy+6cvgNZz2auHSq4wF8WmZxdZAcAGoXqfBDEAR0t7dbGWQY+PEpOXbDw8KDJKKYaMnIWivhco4zSlXLI3PMT4ih2hFW4GQmhKYKmWkuJeQR6+JfILkAqnjD0aTPPFao8OyUakBeKkMohLjplLrxwTiKW2gwfQHgtyKIrycey17YOoUkqtBaV2prbiGJVg2kVaLqMpPHEsI29/VrENQRQF+gyvbgBaQZ2EokxiAswipNhGmwxz3pTmwAvCBEAqI90HSDWVFf6hgm4bCJAGpmJvXnGMOVI92RZJFRAibqIjNElYoACS4FMpFMej+f4BUHFDRHGQKWybjP4IYTHAepZPg9YYyujZ2I+EShKj4VBShVYAU/fQj+1mfEMCeRh0g1UfRGwIaHhkiQb292Dnbatfn5/N3NozGNS1ORhE4ycov76+gmWypHJHVZegH18b1Ruvn5/L/phwEaQYCBkdsAXp1d35akmTgx2rtekT3REima3352SZfc0ICY0U7EliQ+yatPfKWqV8o0X09d6P/U7YMTkzupXsPMsoSO25PBI8WGNnspJPPSrTdAOpQTlWYNQR7sQSonDlwkxbJKXmVcPxatdbbfAwhVt7KMvzPGEGEDpRbbhHUo6ogqfZkl0h1ix2aoVgRrmAPQXnkpFxSlNAIi4+Z63CvNJqrV0nG27LsehXX7aorZk0TQJA6dW6fJOb1q2HyWp42EAesCvdgv14hEd/0TThUxtvCO0w+SPvyry+9qC0tloASGNab7ewlAdu7UaP4iaL4YQL1NrC399HBtm7VTzD78ZAkZ2OD/Xq/bHtdN/3j0kGZwSgzuS/v3tAByMZLbQsok/3r4dCPW3/wCV46pldFgCqp4E4ll6kBiB0XvErVG127q/w7NPHC8sxCwxlhEVaT95ujbUGazxbocOiFyyF8NwfWM88xoeSTpLy06T1kh0iyVHZsTN2bcDou+NCiHW5I6gDv0/ZYSkzRS4RuYjgcIUwkdyYWuNKCcCZNwJDRwppjHgoGSbGrM7yMvCpLyFl99aPY2WyG/dOXW5jkplvlLoAPl4xccznotYxPgdYXif/fwhR8pe+yVeuMvK8GVzgnUoRkkQGhAn/YkrG+Tu0XGSmAqAwvpGBgC4I7gMerAFAZhdAjWkh/jAgBYF48IgAiUnDCH3EhFke3wB2YlMSvxAljhjMmZc/LSuMwbFCoEbmvZwqL4AkBSJ3pcj+bRhPcfTmfIzjmCfDGQA/tRWJPwCFOCWzYe6yJ+7iT3YnJz+Ncx6emu4yekb9y8OvD2Sk/im+//mXhz/60Rv1Z1P99vD7SIaN+3N+tcnbDv9fzGgeZ/5sXn+jZf8D5vFZIZ+pzf0AAAAASUVORK5CYII=");
        }
        .podcastlinux{
            background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAMAAABg3Am1AAAAYFBMVEW6Sg27URzJYBnAZjrKaS/LfErLhWPZmV7Vm2/SnHngrH/csY/auKTJy8jZyL3gybfhyL/ez8vf0cXS1NHm2N/b3Nnl29Lc3+Lh4d7s49zl6Ovn6ebt8O3y9PH4+vf9//xpIPITAAAAAWJLR0QAiAUdSAAAAAlwSFlzAAAN1wAADdcBQiibeAAAAAd0SU1FB+EFBQosLgaC/nIAAABBdEVYdENvbW1lbnQAQ1JFQVRPUjogZ2QtanBlZyB2MS4wICh1c2luZyBJSkcgSlBFRyB2NjIpLCBxdWFsaXR5ID0gODIKg7FQJgAAApdJREFUSMe1lguzmjAQhUNRL5BISriQlWTj//+X3c1DENS2M+1BYQbPx9k8SBT3v5T4F0AgISKd/whg76rwGyCg9xs3J4UPANtZiIWKgeEdkO2ZKQTdx9fA1l+CfHz8NuQBBO9IByS1O6yEePIfCR9iRcHvgew/QuH+TGQA3U5rRiFwCwR31NqMRORmiLUgpGE4IiE66ZuLEo+CAp0RDymrOw2HKAHJusugGzQVadwDu30BYgswufetp3uP7oqtEKUidBzuEN41H1NHMZAeBTHLOyC5xS30eUYwRohcEdCgEorRD7DM823Zx2AGUtngeSJnv13akzrrPfIA6IfoSnZLBwGEcFWpuKjYxwT45bbAYgG0YTd/NDQnJXtttIJB3Zw2SrtvNWMCwBhrDMydHoZ5MEabs6SEH+3pVImLEtpVzaVSdWUyoL+aTtLRdI1su6ZppDQJqHV9UlV/qy63mllTgK6TRDRfUn8p8jdSNxFoF3qy6F3Vuouo6lqlRpvOgFQg5dQpo6SWWhfAMtBK0aqqFpcllYSzsdxFjjvDsiZr27M8tefWNvVc06Mv9flGbB44S/1CHTux6GL5OvSmH/RIVxioL/p+WODnkIB7nAxTlucTMTlpmif7zX0dH5oBD8A2uhEzIjHGoHlKeTYOj13K9I4BjAeqy42kgY4puzNDRJmtd0cApMVgGmF8VqmV6l5fUQJcWg2m0Y1viOnxxlEl/gNQENisGhwRX3H3yp8R3C5kPAyeXqURpvGN3PNSCWngIDX5Soqn65oRdosxjx7n+uxcNUYKD8t9qgXd9ZXGcNxQEnE9BEQ/vtqBgivl7wXhzaaIL+1X/2HbdUcEPm/swcOGGeOU/N1fB1rQ0nrpMfynPycf9QuEruKuulaDHwAAAABJRU5ErkJggg==");
        }
        .salmorejogeek{
            background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAMAAABg3Am1AAAAYFBMVEUcGxwmJSgiJzQ2NTM3RVQ9VYJuUShYVlNEZlJGY8BdZm5IartvcnFQdv9SfrxTfP9Whv+Hhn6Ck51hmP/gkzZpqv9wtv61tKp5v/1k2YjovEvYxHnDxcK60uTy5b3x69cOzPdIAAAAAWJLR0QAiAUdSAAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB+EFBQoyB5BxWcEAAAHiSURBVEjHldTrmqMgDAbgcCpbZT12prP24P3f5SRKEAWfsl9/1eZtCNDCuOYrl2/OzxYY/1ME8EF8p6BQRCBPjmIHSsQeFIi0Q9MY0zSnm3WYwUjQFUaDNPkeMWiMqoaXz1Ap02REBIwO1d5ok4oNCPdK4mQiGNRieGUyiOOyPKhVtj4joOuW9ZzUY+R+s1Yg1/UPlGQOvRMIutHY5RMlAECo4/DW/GAhiwVIeq6ED6ituAIfwz0I1BUNtwWE48VVf3z4RJYZ6MCUiLN+K+6E++cTjpA6iGP9kuWaBKAjUFtcqqDX1oEvVRYYhwNcbrfLVl+FPc0BOViqv91C/XYWeeBAUf10gXXg6OzyQAA1mKZJ4dbYvrcZYHaABNZPD9s/3u93Xw0cGzo0/meLQAOd1QXrH1T+nmelrI9igE+U4V1a91OF+rl3T5+wJHziGNT+AOC+ln8AbdfxiaGYC0DLaxLCzkWgvYZLcT8Cy7d1BzrNa+qPoOKv2oHQIgVxIhCmcIWg7STEU5+CkUFL96OgA/7BeNBeqQeUgL9e0Bwfh14Ai7YGuBeB0KMz0t2fT/xBWLemX+LfWLziK4jI1RgN5xEMwrLQ4BafRgawCSKUMc0Xz0D1qdiyU6FDqWBwmONc/AL0UaQcBFX61wAAAABJRU5ErkJggg==");
        }
        .ugeek{
            background-image: url("data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAMAAABg3Am1AAAAYFBMVEVVMZZcL5ljMJVdM5VlMphnNJllNpNtNpdxOZt4PJiCPZ2KQZ2RRJyYRJ+gSJ+oTJ6vTKK3UaK/UKXFVKPOVKjMWaPVWajcWKrbXKXkXarqYKjyYKz1Y67/ZK76Zqz+aq9CAXa/AAAAAWJLR0QAiAUdSAAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB+EFBQorIK57RbIAAAF5SURBVEjH7ZVhc4MgDIYrHEMEI5rikEr8//9ytLVrxR12X3d7T4RwPJhwJJ7YL3X6SwDXRckcgLjEkpZBbABNh7IbAAl4yfMq7fgKVCHqbImQG1Mui3wFptjcBsp7dV9R+xz4yAHVKO2lrGtn2DDIUbcHQKs19HxAp6YOLAbkbwCOC/QAPVgT8Mgl6Zxs3aiNQ+WcQdOLMsCqam337jDox3k+9oWXMy4AYoJRpXC59BXnLD1VGhaBUweTV3im2o96DDZ4S6oAfAbEhuEoPEiGAqxHGcpfYIDQTpq0NZ1xQ4f9pRS0Sa0FVvfAAVjXKug4lICfJSkDCIeydkA80A4Y+q1sZmZAyGOYqBhDStFObNSft7ahmb8CTcryjcd7G7ZlRoflKYrXd7x36xTkheyUcnOVitPVwGi/5xQvlUoXb8nWRnqvtipabpWDX8i8BYw0rLcqknwD8M9lY7zIA2Ca54Xmhy4Uk6FKgJ93CnXZJbHTH/4p/gMFfQHdIENuISGquQAAAABJRU5ErkJggg==");
        }
        body{
            background-color: rgb(247, 247, 247);
            font-family: "Roboto", sans-serif;
            body { background-image:
            background.image: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='10' height='10'><linearGradient id='gradient'><stop offset='10%' stop-color='%23F00'/><stop offset='90%' stop-color='%23fcc'/> </linearGradient><rect fill='url(%23gradient)' x='0' y='0' width='100%' height='100%'/></svg>");
      }
        }
        .panel{
            webkit-box-shadow: 0 0 1px rgba(0, 0, 0, 0.15);
            -moz-box-shadow: 0 0 1px rgba(0, 0, 0, 0.15);
            box-shadow: 0 0 1px rgba(0, 0, 0, 0.15);
            box-sizing: border-box;
            display: block;
            min-height: 70px;
            background-color: #fff;
            padding: 10px;
            margin: 0 auto;
            margin-bottom: 20px;
        }
        audio {
            width:250px; /* Ancho del reproductor */
            display: block;
            float:left;
        }
        ul {
          list-style-type: none;
          padding-left: 0px;
        }
        li {
            list-style-type: none;
            height:70px;
        }
        span[id^="item-"]{
            height:48px;
            line-height: 20px;
            display: block;
            }
        .isplaying{
            float:left;
            margin-top:12px;
            width:24px;
            height:24px;
            margin-right: 5px;
        }
        .logo{
            float:left;
            width:48px;
            height:48px;
            margin-right: 5px;
        }
        .podcast, #podcast{
            display: block;
            font-size: 16px;
            font-weight: 400;
            color:rgba(0,0,0,.87);
            }
        .track, #track{
            display: block;
            font-size: 14px;
            font-weight: normal;
            color:rgba(0,0,0,.54);
        }
        #track{
            text-overflow: ellipsis;
            display: -webkit-box;
           -webkit-box-orient: vertical;
           -webkit-line-clamp: 2;
        }
        #player{
            height:80px;
            float:left;
        }
        #playing{
            height:80px;
            float:left;
        }
        .playingnow{
            font-size: 12px;
            color: #9E9E9E;
        }
        a{
            text-decoration:none;
            color:rgba(0,0,0,.54);
        }
        a:visited{
            text-decoration: none;
            color:rgba(0,0,0,.54);
        }
        @media only screen and (min-width: 700px) {
            .panel{
                width:600px;
            }

        }
    </style>
</head>
<body>
    <div class="panel">
        <div id="player">
            <a href="#" id="left" onclick="return false" title="Anterior">
                <i class="fa fa-chevron-left" aria-hidden="true"></i>
            </a>
            <audio id="audio" preload="auto" tabindex="0" controls="">
                <source src="">
            </audio>
            <a href="#" id="right" onclick="return false" title="Siguiente">
                <i class="fa fa-chevron-right" aria-hidden="true"></i>
            </a>
        </div>
        <div id="playing">
            <span class="playingnow">Reproduciendo ahora...</span>
            <span id="podcast"></span>
            <span id="track"></span>
        </div>
    </div>
    <div class="panel">
        <ul id="playlist">

<li class="active">
	<span id="item-0">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/05/podcast-27-ipv6-primera-parte.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #27: IPv6 (primera parte)</span>
		</a>
	</span>
</li>
<li>
	<span id="item-1">
		<a href="https://ia601506.us.archive.org/33/items/JekyllOWordpress/Jekyll%20o%20Wordpress.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">052. ¿Jekyll o WordPress?</span>
		</a>
	</span>
</li>
<li>
	<span id="item-2">
		<a href="https://ia801502.us.archive.org/5/items/051.AdisBloggerHolaGithub/051.%20Adi%C3%B3s%20Blogger,%20Hola%20Github%20.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">051. Adiós Blogger, Hola GitHub!</span>
		</a>
	</span>
</li>
<li>
	<span id="item-3">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/05/podcast-26-odoo-y-transformacion.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #26: Odoo y transformación digital</span>
		</a>
	</span>
</li>
<li>
	<span id="item-4">
		<a href="http://www.ivoox.com/119-geekeando-erika-betancor_mf_18422071_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#119 Geekeando con Érika Betancor</span>
		</a>
	</span>
</li>
<li>
	<span id="item-5">
		<a href="https://ia801505.us.archive.org/9/items/050.QueAndoHaciendo/050.%20Que%20ando%20haciendo.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">050. Que ando haciendo, nuevas publicaciones y más...</span>
		</a>
	</span>
</li>
<li>
	<span id="item-6">
		<a href="http://www.ivoox.com/118-directo-asi-estan-cosas-abril-2017_mf_18412331_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#118 Directo: Así están las cosas (Abril 2017)</span>
		</a>
	</span>
</li>
<li>
	<span id="item-7">
		<a href="https://ia601503.us.archive.org/0/items/049.Syncthing/049.%20Syncthing.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">049. Instalando Syncthing en Ubuntu, Antergos y Raspberry Pi</span>
		</a>
	</span>
</li>
<li>
	<span id="item-8">
		<a href="http://compilando.audio/wp-content/uploads/2017/04/podcast4.mp3">
			<span class="isplaying"></span>
			<span class="logo compilandopodcast"></span>
			<span class="podcast">Compilando Podcast</span>
			<span class="track">Podcast 4 – Jon “maddog” Hall , Open South Code y Linux y Tapas</span>
		</a>
	</span>
</li>
<li>
	<span id="item-9">
		<a href="https://ia601503.us.archive.org/28/items/EncuentroDeAmiguetes/Encuentro%20de%20amiguetes.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">048. Encuentro de amiguetes</span>
		</a>
	</span>
</li>
<li>
	<span id="item-10">
		<a href="http://www.ivoox.com/twitter-sabemos-usarlo-android-audio-pocket-casts_mf_18349090_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Twitter, ¿sabemos usarlo? Android Audio y Pocket Casts</span>
		</a>
	</span>
</li>
<li>
	<span id="item-11">
		<a href="http://www.ivoox.com/23-la-terminal_mf_18347303_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#23 La Terminal</span>
		</a>
	</span>
</li>
<li>
	<span id="item-12">
		<a href="https://ia801500.us.archive.org/21/items/SeEstropeaLaSDDeMiRasberry/Se%20estropea%20la%20SD%20de%20mi%20rasberry.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">047. Se quemó la SD. Comparación de consumos entre PC, NAS-Microserver, Raspberry Pi</span>
		</a>
	</span>
</li>
<li>
	<span id="item-13">
		<a href="http://www.ivoox.com/117-sin-sombra-helicoptero_mf_18309317_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#117 Sin sombra en el helicóptero</span>
		</a>
	</span>
</li>
<li>
	<span id="item-14">
		<a href="http://www.ivoox.com/116-conociendo-deepin-gnu-linux-15-4_mf_18295101_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#116 Conociendo Deepin GNU Linux 15.4</span>
		</a>
	</span>
</li>
<li>
	<span id="item-15">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/04/podcast-25-introduccion-a-docker.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #25: Introducción a Docker</span>
		</a>
	</span>
</li>
<li>
	<span id="item-16">
		<a href="https://ia601509.us.archive.org/6/items/046SyncthingResilioYDukto/%23046%20Syncthing%2c%20Resilio%20y%20Dukto%20.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">046. Sincronización de carpetas entre dispositivos. Syncthing, Resilio y Dukto</span>
		</a>
	</span>
</li>
<li>
	<span id="item-17">
		<a href="https://ia801502.us.archive.org/1/items/041UbuntuYElAdiosAUnity/%23041%20Ubuntu%20y%20el%20adi%c3%b3s%20a%20Unity.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">041. Ubuntu y el adios de Unity</span>
		</a>
	</span>
</li>
<li>
	<span id="item-18">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/04/podcast-24-sobre-vlans.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #24: Sobre Vlans</span>
		</a>
	</span>
</li>
<li>
	<span id="item-19">
		<a href="http://www.ivoox.com/seguridad-hardware-tu-servidor-casero_mf_18128440_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Seguridad por Hardware en tu Servidor casero</span>
		</a>
	</span>
</li>
<li>
	<span id="item-20">
		<a href="http://www.ivoox.com/115-crossover-ugeek-podcast-mastodon-ubuntu-y_mf_18112915_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#115 Crossover con uGeek Podcast: Mastodon, Ubuntu y comunidad Linux, Telegram y mucho más</span>
		</a>
	</span>
</li>
<li>
	<span id="item-21">
		<a href="http://www.ivoox.com/22-linux-connexion-osl-la_mf_18133189_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#22 Linux Connexion con la OSL de la Universidad de La Laguna</span>
		</a>
	</span>
</li>
<li>
	<span id="item-22">
		<a href="https://ia801505.us.archive.org/27/items/045CrossoverConSalmorejoGeek/%23045%20Crossover%20con%20Salmorejo%20Geek.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">045. Crossover con Salmorejo Geek, donde hablamos de Mastodon, Ubuntu, Telegram y mucho mas...</span>
		</a>
	</span>
</li>
<li>
	<span id="item-23">
		<a href="https://ia801504.us.archive.org/22/items/044WebDeJekyllEnGithub/%23044%20Web%20de%20Jekyll%20en%20Github.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">044. La web de Jekyll en GitHub, va tomando forma</span>
		</a>
	</span>
</li>
<li>
	<span id="item-24">
		<a href="http://www.ivoox.com/114-ubuntu-abandona-unity-convergencia-y_mf_18057325_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#114 Ubuntu abandona Unity y la Convergencia ¿Y ahora qué?</span>
		</a>
	</span>
</li>
<li>
	<span id="item-25">
		<a href="https://ia601509.us.archive.org/23/items/043BotDeTelegramDeIFTTT/%23043%20Bot%20de%20Telegram%20de%20IFTTT.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">043. Bot de Telegram IFTTT</span>
		</a>
	</span>
</li>
<li>
	<span id="item-26">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/04/podcast-23-calcular-mascaras-de-red.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #23: Calcular máscaras de red</span>
		</a>
	</span>
</li>
<li>
	<span id="item-27">
		<a href="http://www.ivoox.com/que-pasa-ubuntu-hablando-linux-con_mf_18041732_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">¿Qué pasa con Ubuntu? Hablando de Linux con El Atareao y con uGeek</span>
		</a>
	</span>
</li>
<li>
	<span id="item-28">
		<a href="https://ia601502.us.archive.org/25/items/042ElAtareaoVisitaElCrossoverDeLaSemana/%23042%20El%20Atareao%20visita%20el%20Crossover%20de%20la%20Semana.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">042. El Atareao visita el Crossover de la Semana</span>
		</a>
	</span>
</li>
<li>
	<span id="item-29">
		<a href="https://compilando.audio/wp-content/uploads/2017/04/Podcast_3.mp3">
			<span class="isplaying"></span>
			<span class="logo compilandopodcast"></span>
			<span class="podcast">Compilando Podcast</span>
			<span class="track">Podcast 3 – Entrevista con ” el atareao” y el nuevo rumbo de Ubuntu</span>
		</a>
	</span>
</li>
<li>
	<span id="item-30">
		<a href="https://ia801504.us.archive.org/29/items/40AntergosOCNewsDeNextcloudYJekyll/%2340%20Antergos%2c%20OCNews%20de%20Nextcloud%20y%20Jekyll%20.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">040. Antergos, Ocnews De Nextcloud Y Jekyll</span>
		</a>
	</span>
</li>
<li>
	<span id="item-31">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/04/podcast-22-iptables-en-gnu-linux.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #22: NAT en GNU/Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-32">
		<a href="http://www.ivoox.com/113-offtopiqueando-ando-informatica-semana-santa-chuck_mf_17909300_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#113 Offtopiqueando ando: Informática, Semana Santa y Chuck Norris</span>
		</a>
	</span>
</li>
<li>
	<span id="item-33">
		<a href="https://ia601508.us.archive.org/2/items/039TelegramNotes/%23039%20Telegram%2c%20Notes.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">039. Aplicación Notes de Nextcloud y crea tus bots de Telegram</span>
		</a>
	</span>
</li>
<li>
	<span id="item-34">
		<a href="https://compilando.audio/wp-content/uploads/2017/04/CompilandoPodcast2.mp3">
			<span class="isplaying"></span>
			<span class="logo compilandopodcast"></span>
			<span class="podcast">Compilando Podcast</span>
			<span class="track">Podcast 2 – Especial Servidores Privados</span>
		</a>
	</span>
</li>
<li>
	<span id="item-35">
		<a href="https://compilando.audio/wp-content/uploads/2017/04/podcast_1.mp3">
			<span class="isplaying"></span>
			<span class="logo compilandopodcast"></span>
			<span class="podcast">Compilando Podcast</span>
			<span class="track">Podcast 1- Ian Murdock, Debian y el proyecto QSL</span>
		</a>
	</span>
</li>
<li>
	<span id="item-36">
		<a href="http://www.ivoox.com/virtualizacion-ugeek-mosqueteroweb-face-to-face_mf_17898640_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Virtualizacion. uGeek y Mosqueteroweb. Face to Face.</span>
		</a>
	</span>
</li>
<li>
	<span id="item-37">
		<a href="https://archive.org/download/PODCAST0_201704/PODCAST_0.mp3">
			<span class="isplaying"></span>
			<span class="logo compilandopodcast"></span>
			<span class="podcast">Compilando Podcast</span>
			<span class="track">Podcast 0 – Edición de presentación. Stallman y el síndrome Mi Pueblex.</span>
		</a>
	</span>
</li>
<li>
	<span id="item-38">
		<a href="https://ia601506.us.archive.org/26/items/38CrossoverConMosqueteroWeb/%23%2038%20Crossover%20con%20MosqueteroWeb.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">038. Crossover con MosqueteroWeb. Masterclass de FreeNas, Docker y virtualización mediante Proxmox y Esxi.</span>
		</a>
	</span>
</li>
<li>
	<span id="item-39">
		<a href="http://www.ivoox.com/112-llamadas-voz-telegram-cada-dia_mf_17886542_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#112 Llamadas de voz en Telegram, cada día mejor</span>
		</a>
	</span>
</li>
<li>
	<span id="item-40">
		<a href="https://ia801503.us.archive.org/18/items/037LlamadasDeTelegram/%23037%20Llamadas%20de%20Telegram.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">037. Llamadas de Telegram ya estan aquí. Y 3 bots que os encantaran</span>
		</a>
	</span>
</li>
<li>
	<span id="item-41">
		<a href="https://ia601509.us.archive.org/25/items/036PodcastConFrank/%23036%20podcast%20con%20Frank.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">036. Podcast con Frank de Batería2x100, Servidores Linux y NAS, lo mismo pero  diferente</span>
		</a>
	</span>
</li>
<li>
	<span id="item-42">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/03/podcast-21-lets-encrypt.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #21: Let’s Encrypt</span>
		</a>
	</span>
</li>
<li>
	<span id="item-43">
		<a href="http://www.ivoox.com/21-gnu-linux-universidad_mf_17834272_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#21 GNU/Linux en la Universidad</span>
		</a>
	</span>
</li>
<li>
	<span id="item-44">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/03/podcast-20-como-ganar-dinero-con-el-podcast.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #20: Cómo ganar dinero con el podcast</span>
		</a>
	</span>
</li>
<li>
	<span id="item-45">
		<a href="http://www.ivoox.com/freenas-servidor-hp-gen8-contenedores-y-maquinas_mf_17803755_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">FreeNAS , Servidor HP Gen8, Contenedores Y Máquinas Virtuales</span>
		</a>
	</span>
</li>
<li>
	<span id="item-46">
		<a href="https://ia601501.us.archive.org/10/items/035MiG8/%23035%20Mi%20G8.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">035. Mi HP ProLiant MicroServer Gen8</span>
		</a>
	</span>
</li>
<li>
	<span id="item-47">
		<a href="https://ia801500.us.archive.org/9/items/034BotDeTelegramSustitutoAShazam/%23034%20Bot%20de%20Telegram%20sustituto%20a%20Shazam.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">034. Bots de Telegram Sustitutos a Shazam y busqueda de articulos dentro del bot de Pocket</span>
		</a>
	</span>
</li>
<li>
	<span id="item-48">
		<a href="http://www.ivoox.com/chromebooks-raspi-xiaomi-note-4-ultraportatil-jumper_mf_17764920_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Chromebooks, raspi, Xiaomi Note 4 y ultraportátil Jumper</span>
		</a>
	</span>
</li>
<li>
	<span id="item-49">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/03/podcast-19-openvpn.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #19: OpenVPN</span>
		</a>
	</span>
</li>
<li>
	<span id="item-50">
		<a href="https://ia601500.us.archive.org/4/items/033BotDePocketParaTelegram/%23033%20Bot%20de%20Pocket%20para%20Telegram.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">033. Bots en Telegram. Bot de Pocket</span>
		</a>
	</span>
</li>
<li>
	<span id="item-51">
		<a href="https://ia601606.us.archive.org/30/items/032MiscelaneaDeViernes/%23032%20Miscel%C3%A1nea%20de%20Viernes.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">032. Miscelánea de Viernes</span>
		</a>
	</span>
</li>
<li>
	<span id="item-52">
		<a href="https://ia601606.us.archive.org/14/items/031Keepass.ComoGestionoMisContrasenas/%23031%20Keepass.%20Como%20gestiono%20mis%20contrase%C3%B1as.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">031. Keepass, como gestiono mis contraseñas</span>
		</a>
	</span>
</li>
<li>
	<span id="item-53">
		<a href="https://ia601609.us.archive.org/0/items/030Mumble/%23030%20Mumble.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">030. Mumble, VoIP de Software Libre. Nextcloud, Wallabag y kdenlive</span>
		</a>
	</span>
</li>
<li>
	<span id="item-54">
		<a href="http://www.ivoox.com/111-problemas-focusrite-scarlett-solo-y_mf_17626877_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#111 Problemas con la Focusrite Scarlett Solo y 2i2 en macOS Sierra</span>
		</a>
	</span>
</li>
<li>
	<span id="item-55">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/03/podcast-18-herramientas-simples-y-utiles-para-un-adminsitrador-de-red.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #18: Herramientas simples y útiles para un adminsitrador de red</span>
		</a>
	</span>
</li>
<li>
	<span id="item-56">
		<a href="https://ia601608.us.archive.org/28/items/029MiscelneaDeViernes/%23029%20Miscel%C3%A1nea%20de%20viernes.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">029. Miscelánea de Viernes.</span>
		</a>
	</span>
</li>
<li>
	<span id="item-57">
		<a href="https://ia601607.us.archive.org/17/items/ugeekpodcast_gmail_XMPP/XMPP.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">028. Instala un servidor de mensajeria tipo Whatsapp o Telegram y de Software Libre con XMPP/Jabber</span>
		</a>
	</span>
</li>
<li>
	<span id="item-58">
		<a href="http://www.ivoox.com/20-linux-connexion-david-montalva-lliurex_mf_17557164_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#20 Linux Connexion con David Montalva (Lliurex)</span>
		</a>
	</span>
</li>
<li>
	<span id="item-59">
		<a href="http://www.ivoox.com/110-armando-nuevo-pc-para-linux_mf_17538251_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#110 Armando un nuevo PC para Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-60">
		<a href="https://ia601606.us.archive.org/3/items/027InstalaTuVpnEnUbuntuORaspberryPi/%23027%20instala%20tu%20vpn%20en%20Ubuntu%20o%20Raspberry%20Pi.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">027. Instala una VPN (OpenVpn) en Ubuntu o Raspberry Pi con PiVpn</span>
		</a>
	</span>
</li>
<li>
	<span id="item-61">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/03/podcast-17-sistemas-de-monitorizacion-de-sistemas-y-red.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #17: Sistemas de monitorización de sistemas y red</span>
		</a>
	</span>
</li>
<li>
	<span id="item-62">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/03/podcast-16-directo-11-marzo-2017.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #16: Directo 11 de Marzo 2017</span>
		</a>
	</span>
</li>
<li>
	<span id="item-63">
		<a href="https://ia601606.us.archive.org/25/items/026PodcastConFrankDeBatera2x100/%23026%20Podcast%20con%20Frank%20de%20Bater%C3%ADa2x100.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">026. Podcast con Frank de Batería2x100, Hablamos de como gestionamos nuestras Fotos, actualidad y sorteo del libro del año</span>
		</a>
	</span>
</li>
<li>
	<span id="item-64">
		<a href="http://www.ivoox.com/transexualidad_mf_17427425_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Transexualidad</span>
		</a>
	</span>
</li>
<li>
	<span id="item-65">
		<a href="http://www.ivoox.com/flintos-raspberry-pi-vernee-thor_mf_17416576_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">FlintOS, Raspberry PI y Vernee Thor</span>
		</a>
	</span>
</li>
<li>
	<span id="item-66">
		<a href="https://ia601600.us.archive.org/16/items/025MtodoMMsCompletoQueParaRecopilarNotasOrgMode/%23025%20M%C3%A9todo%20m%C3%A1s%20completo%20que%20para%20recopilar%20notas%2C%20org%20mode.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">025. Metodo mas completo para recopilar notas, org Mode</span>
		</a>
	</span>
</li>
<li>
	<span id="item-67">
		<a href="http://www.ivoox.com/109-mi-vuelta-a-antergos-linux-al-estilo_mf_17415345_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#109 Mi vuelta a Antergos Linux al estilo Atlético de Madrid</span>
		</a>
	</span>
</li>
<li>
	<span id="item-68">
		<a href="https://ia601605.us.archive.org/10/items/024ConectateRemotamenteATuRaspberryPiCondataplicity/%23024%20Conectate%20remotamente%20a%20tu%20Raspberry%20Pi%20con%20%22dataplicity%22%20.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">024. Conectate remotamente a tu Raspberry Pi con "dataplicity"</span>
		</a>
	</span>
</li>
<li>
	<span id="item-69">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/03/podcast-15-mumble.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #15: Mumble, tu mesa de reuniones virtual</span>
		</a>
	</span>
</li>
<li>
	<span id="item-70">
		<a href="http://www.ivoox.com/108-directo-asi-estan-cosas-marzo_mf_17354573_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#108 Directo - Así están las cosas (Marzo 2017)</span>
		</a>
	</span>
</li>
<li>
	<span id="item-71">
		<a href="https://ia801609.us.archive.org/20/items/EntrevistaADosDesarrolladoresDeSoftwareLibreDeIgalia/Entrevista%20a%20dos%20desarrolladores%20de%20Software%20Libre%20de%20Igalia.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">023. Entrevista a Chema y Juan, dos desarrolladores de Software Libre de Igalia.com en el #mwc17</span>
		</a>
	</span>
</li>
<li>
	<span id="item-72">
		<a href="https://ia601600.us.archive.org/33/items/EntrevistaConArturoSuarezDirectivoDelCloudDeCanonicalUbuntu/Entrevista%20con%20Arturo%20Suarez,%20Directivo%20del%20Cloud%20de%20Canonical%20Ubuntu.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">022. Entrevista con Arturo Suarez, DIrectivo del Cloud de Canonical Ubuntu</span>
		</a>
	</span>
</li>
<li>
	<span id="item-73">
		<a href="http://www.ivoox.com/19-gnu-linux-escuela_mf_17289281_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#19 GNU/Linux en la escuela</span>
		</a>
	</span>
</li>
<li>
	<span id="item-74">
		<a href="http://www.ivoox.com/amd-vs-intel-samsung-nokia-mwc-spotify-cloudflare_mf_17285109_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">AMD vs Intel. Samsung. Nokia MWC Spotify Cloudflare Martingala</span>
		</a>
	</span>
</li>
<li>
	<span id="item-75">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/02/podcast-14-radio-o-podcast.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #14: Radio o Podcast, no elijas puedes tener las dos</span>
		</a>
	</span>
</li>
<li>
	<span id="item-76">
		<a href="https://ia801606.us.archive.org/21/items/021UbuntuEnMobileWorldCongress/%23021%20ubuntu%20en%20Mobile%20World%20Congress%20.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">021. Ubuntu en el Mobile World Congress</span>
		</a>
	</span>
</li>
<li>
	<span id="item-77">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/02/podcast-13-ospf-multiarea.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #13: OSPF Multiárea</span>
		</a>
	</span>
</li>
<li>
	<span id="item-78">
		<a href="https://ia601601.us.archive.org/7/items/20PodcastConFrankDeBatera2x100HablamosDeComoGestionamosNuestraNotas/%2320%20Podcast%20con%20Frank%20de%20Bater%c3%ada2x100%2c%20Hablamos%20de%20como%20gestionamos%20nuestra%20notas%20.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">020. Podcast con Frank de Batería2x100, Hablamos de como gestionamos nuestra notas y mucho mas...</span>
		</a>
	</span>
</li>
<li>
	<span id="item-79">
		<a href="http://www.ivoox.com/noticias-tecnologicas_mf_17193972_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Noticias Tecnológicas</span>
		</a>
	</span>
</li>
<li>
	<span id="item-80">
		<a href="https://ia601603.us.archive.org/6/items/019DokuwikiNuevaFormaDeTomarMisNotas/%23019%20Dokuwiki%2c%20nueva%20forma%20de%20tomar%20mis%20notas%20.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">019. Dokuwiki, nueva forma de tomar mis notas. Monta tu wiki con DokuWiki o MediaWiki.</span>
		</a>
	</span>
</li>
<li>
	<span id="item-81">
		<a href="https://ia601604.us.archive.org/24/items/018WallabagElPocketOInstapaper/%23018_Wallabag%2c_el_Pocket_o_Instapaper.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">018. Como montar Wallabag, el Pocket o Instapaper de software libre y lo mejor de todo, en tu servidor</span>
		</a>
	</span>
</li>
<li>
	<span id="item-82">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/02/podcast-12-atencion-al-cliente-y-migrar-una-web.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #12: Atención al cliente y migrar una web</span>
		</a>
	</span>
</li>
<li>
	<span id="item-83">
		<a href="https://ia801300.us.archive.org/34/items/017PodcastConFrankDeBateria2x100HablandoDePlexNextcloud.../%23017%20Podcast%20con%20Frank%20de%20Bateria2x100%2c%20hablando%20de%20Plex%2c%20Nextcloud....mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">017. Podcast con Frank de Bateria2x100, hablando de Plex, Nextcloud...</span>
		</a>
	</span>
</li>
<li>
	<span id="item-84">
		<a href="https://ia801603.us.archive.org/24/items/016QueEsUnServidor/%23016%20Que%20es%20un%20servidor.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">016. Que es un Servidor (dudas oyentes), servidor web, ...</span>
		</a>
	</span>
</li>
<li>
	<span id="item-85">
		<a href="https://ia801603.us.archive.org/20/items/015AlmacenamientoTheNextcloud/%23015_almacenamiento_the_nextcloud.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">015. Como ampliar el almacenamiento de Nextcloud, combinar con nubes publicas y hacer copias de mis fotos.</span>
		</a>
	</span>
</li>
<li>
	<span id="item-86">
		<a href="http://www.ivoox.com/18-linux-connexion-bitacora-ciberseguridad_mf_17029145_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#18 Linux Connexion con Bitácora de Ciberseguridad</span>
		</a>
	</span>
</li>
<li>
	<span id="item-87">
		<a href="https://ia601602.us.archive.org/11/items/NotasEnNextcloud/Notas%20en%20nextcloud.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">014. Notas en Nextcloud y Markdown</span>
		</a>
	</span>
</li>
<li>
	<span id="item-88">
		<a href="https://ia801601.us.archive.org/21/items/013NewsYFreshRSS.GestorDeNoticiasRSS/%23013%20News%20y%20Fresh%20RSS.%20Gestor%20de%20Noticias%20RSS.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">013. News y FreshRSS. Gestor de Noticias RSS.</span>
		</a>
	</span>
</li>
<li>
	<span id="item-89">
		<a href="https://ia801604.us.archive.org/21/items/013FDroidAplicacionesDeSoftwareLibre/%23013%20F-Droid%20Aplicaciones%20de%20Software%20Libre.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">013. bis F-Droid Tienda Android de aplicaciones de Software Libre y Actualizar las Noticias en Nextcloud.</span>
		</a>
	</span>
</li>
<li>
	<span id="item-90">
		<a href="http://www.ivoox.com/107-no-soy-fanboy_mf_16980247_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#107 No soy un Fanboy</span>
		</a>
	</span>
</li>
<li>
	<span id="item-91">
		<a href="https://ia801601.us.archive.org/24/items/012CmoActualizarNextcloudY/%23012_c%c3%b3mo_actualizar_Nextcloud_y.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">012. Como actualizar Nextcloud y salir del modo de "mantenimiento"</span>
		</a>
	</span>
</li>
<li>
	<span id="item-92">
		<a href="http://www.ivoox.com/w10-no-va-bien-mac-vs-linux-directo_mf_16950998_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">W10 NO va bien. Mac vs Linux. Directo con ChineseDroid+AndroyTecno</span>
		</a>
	</span>
</li>
<li>
	<span id="item-93">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/02/podcast-11-ospf-en-un-area.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #11: OSPF en un único área</span>
		</a>
	</span>
</li>
<li>
	<span id="item-94">
		<a href="https://ia801602.us.archive.org/16/items/011PodcastConFrankDeBateria2x100/%23011%20Podcast%20con%20Frank%20de%20Bateria2x100.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">011. Podcast con Frank de Bateria2x100, hablando un poco de todo...</span>
		</a>
	</span>
</li>
<li>
	<span id="item-95">
		<a href="http://www.ivoox.com/106-linux-no-es-dificil-somos-viejos_mf_16934360_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#106 Linux no es difícil, somos los viejos usuarios quienes lo hacemos así</span>
		</a>
	</span>
</li>
<li>
	<span id="item-96">
		<a href="https://ia601603.us.archive.org/9/items/010ElSistemaOperativoDeBolsillo/%23010%20El%20Sistema%20Operativo%20de%20bolsillo.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">010. CloudReady el Chromium OS de bolsillo</span>
		</a>
	</span>
</li>
<li>
	<span id="item-97">
		<a href="https://ia601602.us.archive.org/11/items/ComoCrearTuPodcastYTotalmenteGtatis/Como%20crear%20tu%20podcast%20y%20totalmente%20gtatis.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">009. Crea tu podcast en 3 simples pasos y totalmente gratis</span>
		</a>
	</span>
</li>
<li>
	<span id="item-98">
		<a href="https://ia801900.us.archive.org/13/items/008ComoGestionoMisNotas/%23008%20Como%20gestiono%20mis%20notas.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">008. Como gestiono mis Notas</span>
		</a>
	</span>
</li>
<li>
	<span id="item-99">
		<a href="http://www.ivoox.com/batiburrillo-androytecno_mf_16862300_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Batiburrillo con AndroyTecno</span>
		</a>
	</span>
</li>
<li>
	<span id="item-100">
		<a href="hhttps://ia601902.us.archive.org/28/items/007LinuxEsUnaAlternativaReal/%23007%20Linux%20es%20una%20alternativa%20real.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">007. Linux es una alternativa real</span>
		</a>
	</span>
</li>
<li>
	<span id="item-101">
		<a href="https://ia601900.us.archive.org/18/items/ElTrelloDeSoftwareLibreWekan/El_Trello_de_software_libre_Wekan.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">006. El Trello de Software Libre Wekan y Kanboard para Raspberry Pi. El sistema Kanban en tu servidor.</span>
		</a>
	</span>
</li>
<li>
	<span id="item-102">
		<a href="http://www.ivoox.com/105-directo-asi-estan-cosas-febrero-2017_mf_16815748_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#105 #Directo Así están las cosas (Febrero 2017)</span>
		</a>
	</span>
</li>
<li>
	<span id="item-103">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/02/podcast-10-dns-y-arp.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #10: Cómo funciona el DNS</span>
		</a>
	</span>
</li>
<li>
	<span id="item-104">
		<a href="https://ia601603.us.archive.org/9/items/005PaperDeDropbox/%23005%20Paper%20de%20Dropbox.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">005. Paper de Dropbox</span>
		</a>
	</span>
</li>
<li>
	<span id="item-105">
		<a href="http://www.ivoox.com/17-linux-connexion-alexandre-filgueira_mf_16768269_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#17 Linux Connexion con Alexandre Filgueira</span>
		</a>
	</span>
</li>
<li>
	<span id="item-106">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/01/podcast-9-streaming-con-icecat2-mp3.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #9: Streaming con Icecast 2</span>
		</a>
	</span>
</li>
<li>
	<span id="item-107">
		<a href="https://ia601903.us.archive.org/19/items/004ServidorLinuxVsQNapSynology/%23004%20Servidor%20Linux%20Vs%20QNap-Synology.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">004. Servidor Linux Vs QNAP-Synology</span>
		</a>
	</span>
</li>
<li>
	<span id="item-108">
		<a href="https://ia601903.us.archive.org/4/items/003Nextcloud/%23003%20Nextcloud.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">003. Nextcloud. Instalar tu Nube en menos de 2 minutos.</span>
		</a>
	</span>
</li>
<li>
	<span id="item-109">
		<a href="https://ia801904.us.archive.org/20/items/DeQueVaEstoDeUGeek/De%20que%20va%20esto%20de%20uGeek%3f.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">002. "De qué va esto de uGeek?"</span>
		</a>
	</span>
</li>
<li>
	<span id="item-110">
		<a href="https://ia801602.us.archive.org/21/items/HolaMundo_201701/Hola%20Mundo.mp3">
			<span class="isplaying"></span>
			<span class="logo ugeek"></span>
			<span class="podcast">uGeek</span>
			<span class="track">001. Hola Mundo</span>
		</a>
	</span>
</li>
<li>
	<span id="item-111">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/01/podcast-8-el-viaje-de-cargar-una-web.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #8: El viaje de cargar una web</span>
		</a>
	</span>
</li>
<li>
	<span id="item-112">
		<a href="http://www.ivoox.com/104-probando-3-cacharros-amazon-adaptadores-wifi_mf_16547697_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#104 Probando 3 cacharros de Amazon: Adaptadores Wifi, Bluetooth y disco duro Sata</span>
		</a>
	</span>
</li>
<li>
	<span id="item-113">
		<a href="http://www.ivoox.com/16-antergos_mf_16451726_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#16 Antergos</span>
		</a>
	</span>
</li>
<li>
	<span id="item-114">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2017/01/podcast-7-cableado.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #7: Cableado en un Centro de Datos</span>
		</a>
	</span>
</li>
<li>
	<span id="item-115">
		<a href="http://www.ivoox.com/15-linux-connexion-jen0f0nte_mf_15880251_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#15 Linux Connexion con Jen0f0nte</span>
		</a>
	</span>
</li>
<li>
	<span id="item-116">
		<a href="http://www.ivoox.com/103-esto-se-va-a-descontrolar-sobre-tuxlibanes_mf_15817492_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#103 Esto se va a descontrolar: Sobre tuxlibanes, blogs linuxeros y sus comunidades</span>
		</a>
	</span>
</li>
<li>
	<span id="item-117">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2016/12/podcast-6-almacenamiento.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #6: Almacenamiento</span>
		</a>
	</span>
</li>
<li>
	<span id="item-118">
		<a href="http://www.ivoox.com/102-balance-linuxero-2016-deseos-para-2017_mf_15446331_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#102 Balance linuxero 2016 y deseos para 2017 por el Killall Radio Podcast Team</span>
		</a>
	</span>
</li>
<li>
	<span id="item-119">
		<a href="http://www.ivoox.com/14-especial-slimbook-katana_mf_15380402_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#14 Especial Slimbook Katana</span>
		</a>
	</span>
</li>
<li>
	<span id="item-120">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2016/12/podcast-5-cloud-centros-de-datos.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #5: Introducción al Cloud y servicios de Centros de Datos</span>
		</a>
	</span>
</li>
<li>
	<span id="item-121">
		<a href="http://www.ivoox.com/101-linux-uefi-gpt-mbr-los_mf_15114926_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#101 Linux en UEFI GPT MBR y los instaladores de las distribuciones</span>
		</a>
	</span>
</li>
<li>
	<span id="item-122">
		<a href="http://www.ivoox.com/13-ciberseguridad-basica-gnu-linux_mf_14880771_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#13 Ciberseguridad Básica en GNU/Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-123">
		<a href="http://www.ivoox.com/100-engrasando-ubuntu-a-vueltas-la_mf_14836526_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo salmorejogeek"></span>
			<span class="podcast">Salmorejo Geek</span>
			<span class="track">#100 Engrasando con Ubuntu, a vueltas con la distro única</span>
		</a>
	</span>
</li>
<li>
	<span id="item-124">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2016/12/podcast-4-ssl-spam-postventa-de-apple.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #4: SSL, spam y postventa de Apple</span>
		</a>
	</span>
</li>
<li>
	<span id="item-125">
		<a href="http://www.ivoox.com/w10-2gb-moto-mods-no-raid_mf_14773966_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">W10 +2GB Moto Mods, No Raid</span>
		</a>
	</span>
</li>
<li>
	<span id="item-126">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2016/12/podcast-3-como-crear-un-podcast.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #3: Cómo crear un podcast</span>
		</a>
	</span>
</li>
<li>
	<span id="item-127">
		<a href="http://www.ivoox.com/12-linux-connexion-alejandro-lopez-slimbook_mf_14164009_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#12 Linux Connexion con Alejandro López ( Slimbook )</span>
		</a>
	</span>
</li>
<li>
	<span id="item-128">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2016/12/podcast-2-crud-en-rails-formularios-dinamicos.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #2: Git, CRUD en Rails y Formularios dinámicos en HTML con JavaScript</span>
		</a>
	</span>
</li>
<li>
	<span id="item-129">
		<a href="http://www.ivoox.com/11-linux-connexion-gabriel-viso-pitando-net-podcast_mf_13759097_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#11 Linux Connexion con Gabriel Viso (Pitando.net). Podcast Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-130">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2016/12/podcast-1-presentacion-rails-lynda.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #1: Presentación, Rails y Lynda.com</span>
		</a>
	</span>
</li>
<li>
	<span id="item-131">
		<a href="https://media.blubrry.com/eduardocollado/www.eduardocollado.com/wp-content/uploads/2016/12/podcast-0.mp3">
			<span class="isplaying"></span>
			<span class="logo eduardocollado"></span>
			<span class="podcast">Eduardo Collado</span>
			<span class="track">Podcast #0: Presentación</span>
		</a>
	</span>
</li>
<li>
	<span id="item-132">
		<a href="http://www.ivoox.com/10-raspberry-pi-gnu-linux-podcast-linux_mf_13546779_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#10 Raspberry Pi y GNU/Linux. Podcast Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-133">
		<a href="http://www.ivoox.com/linux-ha-vencido-cuidado-linux_mf_13467162_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Linux ha vencido! Cuidado con Linux!</span>
		</a>
	</span>
</li>
<li>
	<span id="item-134">
		<a href="http://www.ivoox.com/moviles-servidor-casero_mf_13366716_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Móviles y Servidor Casero</span>
		</a>
	</span>
</li>
<li>
	<span id="item-135">
		<a href="http://www.ivoox.com/09-especial-lenovo-thinkpad-x220_mf_13265714_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#09 Especial Lenovo ThinkPad X220</span>
		</a>
	</span>
</li>
<li>
	<span id="item-136">
		<a href="http://www.ivoox.com/08-sabores-a-montones_mf_13103580_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#08 Sabores a montones</span>
		</a>
	</span>
</li>
<li>
	<span id="item-137">
		<a href="http://www.ivoox.com/distribuciones-linux-recomendaciones_mf_13011221_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Distribuciones Linux. Recomendaciones</span>
		</a>
	</span>
</li>
<li>
	<span id="item-138">
		<a href="http://www.ivoox.com/07-linux-connexion-huezo-grupo-telegram_mf_12912418_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#07 Linux Connexion con Huezo (Grupo Telegram GNU-Linux)</span>
		</a>
	</span>
</li>
<li>
	<span id="item-139">
		<a href="http://www.ivoox.com/07-linux-connexion-huezo-grupo-telegram-gnu-linux_mf_13383404_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#07 Linux Connexion con Huezo (Grupo Telegram GNU/Linux) Podcast Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-140">
		<a href="http://www.ivoox.com/verano-tecnologia_mf_12810335_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Verano y Tecnología.</span>
		</a>
	</span>
</li>
<li>
	<span id="item-141">
		<a href="http://www.ivoox.com/06-conlinuxsisepuede_mf_12737297_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#06 #ConLinuxSíSePuede</span>
		</a>
	</span>
</li>
<li>
	<span id="item-142">
		<a href="http://www.ivoox.com/06-conlinuxsisepuede-podcast-linux_mf_13383405_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#06 #ConLinuxSíSePuede. Podcast Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-143">
		<a href="http://www.ivoox.com/05-linux-connexion-yoyo-fernandez_mf_12593330_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#05 Linux Connexion con Yoyo Fernández</span>
		</a>
	</span>
</li>
<li>
	<span id="item-144">
		<a href="http://www.ivoox.com/05-linux-connexion-yoyo-fernandez_mf_13383406_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#05 Linux Connexion con Yoyo Fernández</span>
		</a>
	</span>
</li>
<li>
	<span id="item-145">
		<a href="http://www.ivoox.com/04-amor-distro-madre_mf_12520959_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#04 Amor de (Distro) madre</span>
		</a>
	</span>
</li>
<li>
	<span id="item-146">
		<a href="http://www.ivoox.com/04-amor-distro-madre-podcast-linux_mf_13383407_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#04 Amor de Distro Madre. Podcast Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-147">
		<a href="http://www.ivoox.com/03-y-no-estaba-muerto-no-no_mf_12374536_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#03 Y no estaba muerto, no no</span>
		</a>
	</span>
</li>
<li>
	<span id="item-148">
		<a href="http://www.ivoox.com/03-y-no-estaba-muerto-no-no-podcast_mf_13383408_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#03 Y no estaba muerto, no, no. Podcast Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-149">
		<a href="http://www.ivoox.com/02-un-pinguino-mi-usb_mf_12218805_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#02 Un pingüino en mi USB</span>
		</a>
	</span>
</li>
<li>
	<span id="item-150">
		<a href="http://www.ivoox.com/02-un-pinguino-mi-usb-podcast-linux_mf_13383409_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#02 Un pingüino en mi USB Podcast Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-151">
		<a href="http://www.ivoox.com/50gb-20euros-audio-mejorado-linea-vacaciones-vodafone-linux-mint-18_mf_12098132_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">50GB-20€ audio Mejorado.Línea vacaciones Vodafone, Linux Mint 18, teclast x89</span>
		</a>
	</span>
</li>
<li>
	<span id="item-152">
		<a href="http://www.ivoox.com/01-antecedentes_mf_12085902_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#01 Antecedentes</span>
		</a>
	</span>
</li>
<li>
	<span id="item-153">
		<a href="http://www.ivoox.com/01-antecedentes-podcast-linux_mf_13383410_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#01 Antecedentes. Podcast Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-154">
		<a href="http://www.ivoox.com/00-promo-podcast-linux_mf_12048502_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#00 Promo Podcast Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-155">
		<a href="http://www.ivoox.com/00-promo-podcast-linux_mf_13383411_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo podcastlinux"></span>
			<span class="podcast">Podcast Linux</span>
			<span class="track">#00 Promo Podcast Linux</span>
		</a>
	</span>
</li>
<li>
	<span id="item-156">
		<a href="http://www.ivoox.com/teclast-x89-kindow-chromebook-otras-noticias_mf_11777780_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Teclast x89 kindow. Chromebook y otras noticias</span>
		</a>
	</span>
</li>
<li>
	<span id="item-157">
		<a href="http://www.ivoox.com/tablet-portatil-2x1-boligrafos-digitales-editores-pdf_mf_11399575_feed_1.mp3">
			<span class="isplaying"></span>
			<span class="logo mosqueteroweb"></span>
			<span class="podcast">MosqueteroWeb</span>
			<span class="track">Tablet + portátil 2x1 Boligrafos digitales Editores pdf</span>
		</a>
	</span>
</li>
        </ul>
    </div>
</body>
</html>
