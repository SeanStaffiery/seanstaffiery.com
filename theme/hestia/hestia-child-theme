<?php                                                                                                                                                          
if ( !defined( 'ABSPATH' ) ) exit;                                                                                                                             
                                                                                                                                                               
if ( !function_exists( 'hestia_child_parent_css' ) ):                                                                                                          
    function hestia_child_parent_css() {                                                                                                                       
        wp_enqueue_style( 'hestia_child_parent', trailingslashit( get_template_directory_uri() ) . 'style.css', array( 'bootstrap' ) );                        
        if( is_rtl() ) {                                                                                                                                       
                wp_enqueue_style( 'hestia_child_parent_rtl', trailingslashit( get_template_directory_uri() ) . 'style-rtl.css', array( 'bootstrap' ) );        
        }                                                                                                                                                      
                                                                                                                                                               
    }                                                                                                                                                          
endif;                                                                                                                                                         
add_action( 'wp_enqueue_scripts', 'hestia_child_parent_css', 10 );                                                                                             
                                                                                                                                                               
/**                                                                                                                                                            
 * Import options from the parent theme                                                                                                                        
 *                                                                                                                                                             
 * @since 1.0.0                                                                                                                                                
 */                                                                                                                                                            
function hestia_child_get_parent_options() {                                                                                                                   
        $hestia_mods = get_option( 'theme_mods_hestia' );                                                                                                      
        if ( ! empty( $hestia_mods ) ) {                                                                                                                       
                foreach ( $hestia_mods as $hestia_mod_k => $hestia_mod_v ) {                                                                                   
                        set_theme_mod( $hestia_mod_k, $hestia_mod_v );                                                                                         
                }                                                                                                                                              
        }                                                                                                                                                      
}                                                                                                                                                              
add_action( 'after_switch_theme', 'hestia_child_get_parent_options' );                                                                                         
                                                                                                                                                               
                                                                                                                                                               
                                                                                                                                                               
add_theme_support( 'yoast-seo-breadcrumbs' );                                                                                                                  
                                                                                                                                                               
// Single post                                                                                                                                                 
add_action( 'hestia_before_single_post_wrap', 'hestia_child_add_yoast_seo_breadcrumbs', 100 );                                                                 
                                                                                                                                                               
// Single page                                                                                                                                                 
add_action( 'hestia_before_page_content', 'hestia_child_add_yoast_seo_breadcrumbs', 100 );                                                                     
                                                                                                                                                               
// Index                                                                                                                                                       
add_action( 'hestia_index_page_before_content', 'hestia_child_add_yoast_seo_breadcrumbs', 100 );                                                               
                                                                                                                                                               
function hestia_child_add_yoast_seo_breadcrumbs() {                                                                                                            
    if ( function_exists( 'yoast_breadcrumb' ) ) {                                                                                                             
        yoast_breadcrumb( '<p id="breadcrumbs">', '</p>' );                                                                                                    
    }                                                                                                                                                          
}                                                                                                                                                              
                                                                                                                                                               
function fb_opengraph() {                                                                                                                                      
    global $post;        
    
      if(is_single()) {                                                                                                                                          
        if(has_post_thumbnail($post->ID)) {                                                                                                                    
            $img_src = wp_get_attachment_image_src(get_post_thumbnail_id( $post->ID ), 'medium');                                                              
        } else {                                                                                                                                               
            $img_src = get_stylesheet_directory_uri() . '/img/opengraph_image.jpg';                                                                            
        }                                                                                                                                                      
        if($excerpt = $post->post_excerpt) {                                                                                                                   
            $excerpt = strip_tags($post->post_excerpt);                                                                                                        
            $excerpt = str_replace("", "'", $excerpt);                                                                                                         
        } else {                                                                                                                                               
            $excerpt = get_bloginfo('description');                                                                                                            
        }                                                                                                                                                      
        ?>                                                                                                                                                     
                                                                                                                                                               
                                                                                                                                                               
<meta property="og:title" content="<?php echo the_title(); ?>"/>                                                                                               
<meta property="og:description" content="<?php echo $excerpt; ?>"/>                                                                                            
<meta property="og:type" content="article"/>                                                                                                                   
<meta property="og:url" content="<?php echo the_permalink(); ?>"/>                                                                                             
<meta property="og:site_name" content="<?php echo get_bloginfo(); ?>"/>                                                                                        
<meta property="og:image" content="<?php echo $img_src; ?>"/>     

/* Documentation from Open Graph Protocol at https://ogp.me/. */                                                                                               
                                                                                                                                                               
<?php                                                                                                                                                          
    } else {                                                                                                                                                   
        return;                                                                                                                                                
    }                                                                                                                                                          
}                                                                                                                                                              
add_action('wp_head', 'fb_opengraph', 5);                    

/* Referenced from: https://www.elegantthemes.com/blog/tips-tricks/how-to-add-open-graph-tags-to-wordpress */
                                                     
                                                                         
