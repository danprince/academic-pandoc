# Introduction

\pagenumbering{arabic}

This is the introduction!

Welcome aboard!

\newpage

![Figure Caption\label{fig:unique-name}](figures/misc/some-figure.pdf)

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam semper ex et metus hendrerit tincidunt. In a nunc ac nisi ultricies gravida quis eget erat. In maximus lacinia ex id vulputate. Vestibulum volutpat porta consequat. Fusce eu magna a nulla accumsan consequat ut quis purus.  

See Figure \ref{fig:unique-name}.

\newpage

~~~{.clojure caption="Listing Caption" label=lst:unique-name}
(defn menu [state]
  (render [this]
    (dom/ul nil
      (map (fn [item]
        (dom/li nil item))
        (:items state)))))
~~~

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aliquam semper ex et metus hendrerit tincidunt. In a nunc ac nisi ultricies gravida quis eget erat. In maximus lacinia ex id vulputate. Vestibulum volutpat porta consequat. Fusce eu magna a nulla accumsan consequat ut quis purus.  

See Listing \ref{lst:unique-name}.

