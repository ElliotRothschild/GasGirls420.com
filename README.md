# GasGirls420.com
Gaming Adult Sexy Streamer Girls 430
function gasgirls_content_shortcode($atts) {
    // Default attributes
    $atts = shortcode_atts(array(
        'type' => 'gaming', // gaming, adult, 420
        'count' => 6
    ), $atts, 'gasgirls_content');

    // Convert type to category slug (adjust based on actual category slugs)
    $category_slug = sanitize_title($atts['type']);

    // WP_Query to fetch videos
    $query = new WP_Query(array(
        'post_type' => 'video',
        'posts_per_page' => intval($atts['count']),
        'tax_query' => array(
            array(
                'taxonomy' => 'video_category',
                'field'    => 'slug',
                'terms'    => $category_slug,
            ),
        ),
    ));

    ob_start();

    if ($query->have_posts()) {
        echo '<div class="gasgirls-video-grid">';
        while ($query->have_posts()) {
            $query->the_post();
            echo '<div class="gasgirls-video-item">';
            echo '<a href="' . get_permalink() . '">';
            if (has_post_thumbnail()) {
                echo get_the_post_thumbnail(get_the_ID(), 'medium');
            }
            echo '<h3>' . get_the_title() . '</h3>';
            echo '</a>';
            echo '</div>';
        }
        echo '</div>';
    } else {
        echo '<p>No videos found for this category.</p>';
    }

    wp_reset_postdata();
    return ob_get_clean();
}
add_shortcode('gasgirls_content', 'gasgirls_content_shortcode');
urn ob_get_clean();
} add_shortcode('gasgirls_content', 'gasgirls_content_shortcode'
